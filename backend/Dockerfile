FROM node:16

# Create app directory
WORKDIR /usr/src/app/backend

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

#Install dependencies
RUN npm install


#Copy the current directory . in the project to the working directory /code in the image.
COPY . .

#Add metadata to the image to describe that the container is listening on port 5000
EXPOSE 5000
CMD [ "node", "server.js" ]
