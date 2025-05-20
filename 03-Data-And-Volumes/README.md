1. Containers have their own filesystems, and data will be deleted when the container is deleted-> PROBLEM
2. Image is read-only so that does not contain runtime data
## Volumes

**Volumes** are folders on our **host machine** stored in our hard drive which would be mounted into containers. Container can read/write into volumes. Volumes persist if containers shut down and when it restart/mount a volume, the data in volume would be available.


```
 docker run -v /app/data => Anonymous volume (data will not be shared with other containers)
 docker run -v volume-name:/app/data => Named volume (data could be shared with other containers)
 docker run -v /app/code:/app/code => Bind mount (volume will be shared with the host)
```

![alt text](image.png)

