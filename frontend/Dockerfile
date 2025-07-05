FROM node:16-alpine as builder

# Set working directory
WORKDIR /app/frontend/

# Copy package.json and package-lock.json to install dependencies
COPY package*.json /app/frontend/
RUN npm install

COPY . /app/frontend/

RUN npm run build

FROM nginx:alpine

# Copy the built files from the previous stage to the nginx directory
COPY --from=builder /app/frontend/build /usr/share/nginx/html
RUN apk add --no-cache bash

EXPOSE 80
