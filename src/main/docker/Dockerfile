# The app runs on port 8080 unless configured
# otherwise.

FROM openjdk:8-jdk-alpine

MAINTAINER Smarter Balanced "opentestsystem.org"

# curl is used for healthcheck
RUN apk add --update curl && rm -rf /var/cache/apk/*

ADD ap-imrt-iss-@version@.jar /

ENV MAX_HEAP_SIZE -Xmx384m

CMD java $MAX_HEAP_SIZE $JAVA_OPTS -jar ap-imrt-iss-@version@.jar
