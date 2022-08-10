#get baseImage
FROM alpine
#use base image to add redis apk on top of it
RUN apk add --update redis
#whenever container is started use the below command to start redis-server
CMD ["redis-server"]
