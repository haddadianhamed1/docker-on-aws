# docker-on-aws
step1 ) test locally
```
npm install --save
node app.js
# use put to increment
curl -X PUT localhost:8080/inc
```

step 2) build image with dockerfile
```
docker build -t hhaddadian/node-hamed .

docker run --rm --publish 8080:8080 --name "sample-service" hhaddadian/node-hamed:latest
or
docker run --rm -d --publish 8080:8080 --name "sample-service" hhaddadian/node-hamed:latest
# to test
curl -X PUT localhost:8080/inc

# localhost:8080 should view number of request

```

step 3 ) create a new cluster

```
aws ecr get-login --no-include-email --region us-west-1

docker build -t hamed .

docker tag hamed:latest 768648327470.dkr.ecr.us-west-1.amazonaws.com/hamed:latest

docker push 768648327470.dkr.ecr.us-west-1.amazonaws.com/hamed:latest
```
