# frontend/Dockerfile
# specify base image
FROM node:21 AS builder
# specify WORKDIR of "node-container"
WORKDIR /app
# copy "host:/${currentDirectory}/frontend//*" to "node-container:/${WORKDIR}"
COPY ./front-end .
# execute command in "node-container:/${WORKDIR}"
RUN npm install && npm run development-build

# multi stage build

FROM nginx:stable-alpine
COPY --from=builder /app/dist /usr/share/nginx/html
COPY ./nginx/nginx.conf /etc/nginx/conf.d/default.conf
