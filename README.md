# docker-images

## Sample docker images 


### DynamoDB 1.0

DynamoDB using Alpine (glibc) distro as base os.

```docker
docker run -p 8000:8000 -v ~/data/db:/var/local_file oocoder/dynamodb 
```
