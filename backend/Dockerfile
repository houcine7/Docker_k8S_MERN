# Base image of our app
FROM node:16-alpine
# application directory inside the image of our app
WORKDIR /src/app/backend
# the environment in which our app is running
ENV NODE_ENV=production
#dependencies installation with npm
#copy package.json and packag-lock.json 
#to the working directory of the app in the image
COPY ["package.json" ,"package-lock.json","./"]
RUN npm install
#  copy source code to the working directory of the app
COPY . .
#to inform docker that the ontainer listens
#on port 5000 at runtime
EXPOSE 5000
#to Run the server 
CMD ["node", "server.js"]
