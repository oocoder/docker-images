FROM oocoder/alpine-oraclejdk:latest
LABEL maintainer="Alex Maldonado <calidadis@gmail.com>"
LABEL version="1.0"
LABEL name="dynamodb"

# Create working space
RUN mkdir /var/dynamodb_wd
WORKDIR /var/dynamodb_wd

# Default port for DynamoDB Local
EXPOSE 8000

# Get the package from Amazon
RUN apk update \                                                                                                                                                                                                                        
    && apk add openssl \
    && wget -O /var/dynamodb_wd/dynamodb_local_latest https://s3-us-west-2.amazonaws.com/dynamodb-local/dynamodb_local_latest.tar.gz \
    && tar xfz /var/dynamodb_wd/dynamodb_local_latest

# Default command for image
ENTRYPOINT ["/usr/bin/java", "-Djava.library.path=.", "-jar", "DynamoDBLocal.jar", "-dbPath", "/var/dynamodb_local"]
CMD ["-port", "8000"]

# Add VOLUMEs to allow backup of config, logs and databases
VOLUME ["/var/dynamodb_local", "/var/dynamodb_wd"]
