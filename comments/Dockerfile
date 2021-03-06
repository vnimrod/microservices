# FROM - The docker image that we want to use as a base.
# Alpine is a term in the docker world for an image as is a small and compact as possible.
# node:alpine - alpine version of node.js, node without alpine, will get extra progrmas that we dont need at this moment.
FROM node:alpine

# WORDDIR - any following commands that we add to our docker will be executed relative to this folder (/app).
# its coming to prevent an accidantly override files that are in the root directory.
WORKDIR /app

# *When we make a chage to any related code that a line in this current Dockerfile is represent, all the lines below that line will be executed from scratch and wont using the cache memory. 
# Adding this copy step before the copy below, is for able to making a change to the code in index.js without re install all node modules again from start, for every code change on index.js.
# The only thing that will execute, RUN npm install again, is changes that we will make to the package.json file. 
# When running the docker build we will see what used cache and what not.
COPY package.json ./

RUN npm install

# COPY - instruction to move files and folders from our local file system to the temporary container file system that is been created during the build process/
# LEFT ./ is the path to folder to copy from on your machine. ./ mean the current working directory .
# RIGHT ./ is the place to copy stuff to inside the container .
COPY ./ ./

CMD ["npm", "start"]