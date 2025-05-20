# Docker Networking

## Container to WWW Communication
- Containers can access the internet by default
- No special configuration needed
- Works out of the box through host's network

```bash
# Example: Testing internet connectivity from container
docker run alpine ping -c 4 google.com
```

## Container to Host Machine Communication
- Use `host.docker.internal` as hostname to reach host machine
- Works on both Windows and macOS
- Common use case for connecting to local databases

```dockerfile
# Example in Dockerfile or container configuration
ENV HOST_URL=http://host.docker.internal:3000
```

## Container to Container Communication
1. **Using Docker Networks (Recommended)**
   ```bash
   # Create a network
   docker network create my-network
   
   # Run containers in the network
   docker run --network my-network --name container1 image1
   docker run --network my-network --name container2 image2
   ```
   - Containers in same network can use container names as hostnames
   - Automatic DNS resolution
   - Isolated and secure

2. **Using Container Links (Legacy)**
   ```bash
   # Not recommended for modern applications
   docker run --link container1:alias container2
   ```

## Network Types
- **bridge**: Default network type, good for single host
- **host**: Shares host's network namespace
- **none**: No networking
- **overlay**: For multi-host networking (Swarm)

## Best Practices
1. Always use custom networks for container communication
2. Use meaningful container names for DNS resolution
3. Avoid exposing ports unless necessary
4. Use environment variables for configuration