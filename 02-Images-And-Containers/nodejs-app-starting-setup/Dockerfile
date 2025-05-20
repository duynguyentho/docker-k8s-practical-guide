FROM node:alpine
# alpine is a lightweight version of the node image
# alpine is a small Linux distribution that is often used as a base image for Docker containers

WORKDIR /app

# copy package.json first to take advantage of Docker cache
COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

# CMD to specific command to run when the container starts
CMD ["node", "server.js"]