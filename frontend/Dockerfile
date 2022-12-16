# Stage 1
# the image base of our forntend app
FROM node:16-alpine3.12 AS builder
# working directory in the container 
WORKDIR /src
# first we copy package*.json to the working dir
COPY ["package.json" ,"package-lock.json","./"]
# install dependencies with npm
RUN npm install
# copy source code of the app
COPY . .
# run and build react app
RUN npm run build


# Stage 2
FROM nginx:1.23.2-alpine
# copy nginx file configuration to the 
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
#remove default nginx static assets
RUN rm -rf /usr/share/nginx/html/*
#copy static assets from builder stage
COPY --from=builder /src/build   /usr/share/nginx/html
#expose container 
EXPOSE 80
#containers run nginx with global directives and daemon off
ENTRYPOINT ["nginx", "-g","daemon off;"]


