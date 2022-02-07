### Microservices

This is an example of running docker images in a microservice architecture using the sample voting app provided by docker.

There are two front ends for this app: 
* voting app
* results app

**Basic Architecture**

* The voting app stores the vote in redis.
* A worker takes the value from redis and persists it into postgres
* The result app queries postgres to show the vote result.

```bash
# start an instance of redis
# -d runs in the background (daemon)
# --name is the name of the container
# the 'redis' param is the image name/version
docker run -d --name=redis redis 
```

```bash
# start an instance of postgres
docker run -d --name=db postgres:9.4
```

```bash
# start an instance of voting app image
docker run -d --name=vote -p 5000:80 dockersamples/examplevotingapp_vote:before
```

```bash
# start an instance of voting app image
docker run -d --name=result -p 5001:80 dockersamples/examplevotingapp_result:before
```

```bash
# start an instance of worker
docker run -d --name=worker dockersamples/examplevotingapp_worker
```

Note:

The redis container is not linked to the voting app. The voting app cannot access the redis instance.

We need to add a `link` argument to the voting app command:

```bash
# add the link option now
docker run -d --name=vote -p 5000:80 --link redis:redis dockersamples/examplevotingapp_vote:before
```

The db container is not linked to the results app. We need to add a link to the result app so it can access the db instance.

```bash
# add a link to the db
docker run -d --name=result -p 5001:80 --link db:db dockersamples/examplevotingapp_result:before
```

The worker container needs a link to both the redis AND db containers
```bash
# add a link to the db and redis
docker run -d --name=worker --link db:db --link redis:redis dockersamples/examplevotingapp_worker
```

Important:
--link will be deprecated. This was just for demo purposes to show how to communicate between containers