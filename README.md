# Link to images on Docker Hub
- [yolo-client](https://hub.docker.com/repository/docker/evelynemwende/yolo-client)
- [yolo-backend](https://hub.docker.com/repository/docker/evelynemwende/yolo-backend)
# Requirements
Make sure that you have the following installed:
- [node](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04) 
- npm 
- [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/) and start the mongodb service with `sudo service mongod start`
## cd into the backend folder and run these commands
    $ cd ../backend

    $ npm install

    $ npm start
## Open a new terminal and navigate to the Client Folder 
    $ cd client

## Run the folllowing command to install the client dependencies 
    $ npm install

## Run the folllowing to start the app
    $ npm start

### Open your browser and visit localhost:3000

### Go ahead and add a product (note that the price field only takes a numeric input)


# Docker

### Create the Docker network to be used
    $ docker network create mongo_network

### Create the Docker volume that will be used
    $ docker volume create mongo_volume

### Navigate into the Project's root directory
    $ cd yolo

### Run docker-compose
    $ docker-compose up

### Open the client/frontend at localhost:3000

### To use custom docker images, edit your docker-compose.yml to look something like this:

      backend:
        image: evelynemwende/yolo-backend:v1.0.1
        build:
            context: backend
            dockerfile: ./Dockerfile
        depends_on:
            - mongo
        ports:
            - 5000:5000
        environment:
            - DB_HOST=mongo
            - DB_USER=admin
            - DB_PASSWORD=password
        volumes:
            - mongo_volume:/data/db
        networks:
            - mongo_network



    client:
        image: evelynemwende/yolo-client:v1.0.1
        build:
            context: client
            dockerfile: ./Dockerfile
        ports:
            - 3000:3000
        stdin_open: true
        tty: true
        depends_on:
            - backend  
        networks:
            - mongo_network
        volumes:
            - mongo_volume:/data/db













