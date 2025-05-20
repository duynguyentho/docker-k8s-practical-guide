#Name image

FROM node:alpine

WORKDIR /app

# copy package.json first to take advantage of Docker cache
COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

# CMD to specific command to run when the container starts
CMD ["node", "server.js"]