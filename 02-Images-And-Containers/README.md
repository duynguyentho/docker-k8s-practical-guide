# Docker Images and Containers

## Images
An image is a blueprint/template for containers. It contains:
- The code/application
- Required runtime environment
- Dependencies and third-party libraries
- Environment variables and settings
- Commands to execute

Images are **read-only** and can be used to create multiple containers. Think of them as a class definition in object-oriented programming.

## Containers
A container is a running instance of an image. It contains:
- An isolated environment with its own filesystem
- A running process based on the image configuration
- Network isolation (can be configured)
- Resource limits (CPU, memory, etc.)

Containers are **writable** and maintain their own state while running. Think of them as objects instantiated from a class.

### Key Differences
| Image | Container |
|-------|-----------|
| Blueprint/Template | Running instance |
| Read-only | Read-write |
| Can exist without containers | Needs an image to run |
| Stored in registries | Runs on Docker host |
| Static | Dynamic |

## Container & Images optimization best practice

 1. use `.dockerignore`
 2. add non-root user
   
```
    RUN addgroup -S appgroup && adduser -S appuser -G appgroup
    USER appuser
```