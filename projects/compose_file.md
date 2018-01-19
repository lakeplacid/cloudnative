---
copyright:
  years: 2017, 2018
lastupdated: "2018-01-19"

---


{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# Compose File
{: #compose-file}

The [Compose](https://docs.docker.com/compose/overview/) file defines information for running multi-container applications.

You should specify the version of Compose file used to be 2.0 or later as such:
`version: '2'`

Services also need to be defined. Here is an example from a Node project:
```
services:
  web:
    build: 
    	context: <path-to-Dockerfile>
	dockerfile: <name-of-Dockerfile>
    tty: true
    command: npm run start-dev
    image: <image-name>
    container_name: <container-name>
    volumes:
      - .:/app
      - /app/node_modules
    ports:
      - "3000:3000"
    links:
      - mongo
    environment:
      MONGO_URL: "mongo"
      MONGO_DB_NAME: "comments"
      NODE_ENV: "development"
      PORT: 3000
  mongo:
    image: mongo
```

`web` and `mongo` are the specified services and each of them has configurations, which are defined in the Docker-Compose [documentation](https://docs.docker.com/compose/compose-file/compose-file-v2/).

The most relevant configurations are listed below:

* build: The context and dockerfile attributes are unnecessary here as they are the default values, but can be overwritten in this format. The context attribute defines the path to the name of the Dockerfile specified in the dockerfile attribute.

* tty: This attribute allows the containers to stay running and not immediately exit. This is required for Docker-Compose support.

* command: This attribute specifies the command to be executed inside the containers.

* image and container_name: These specify the names of the image and containers, respectively.


