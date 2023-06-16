#    Initial before separating dev and production environment.

# #Docker needs to have a base image on the basis of which our image will be generated.
# #node is the base image with 15 as version number
# FROM  node:18
# #this is the working directory of base image (/app) . all the files which we copy will be stored in this dir.
# WORKDIR /app
# # we are copying first package.json to the working directory /app
# COPY package.json .
# #run the command inside image
# RUN npm install
# #copy all files from current directory to the working directory /app
# #first we copied package and then we copied all the files . we did this because docker runs each line of code in layers and caches it.
# # so first package.json is copied and cached and then all the files are coied after installing all the dependencies
# #because package.json doesn't change very frequently . so first we copied it and then focuses on copying other files.
# # so finally if we change the source code and not install any dependencies then only layer-5 (below COPY . .) will run 
# COPY . .
# # assign port 3000 to it . to make environment variables
# ENV PORT 3000
# # this is just for documentation . so that the new developer can see it. $PORT references to PORT variable created above.
# EXPOSE $PORT
# #run the below command on cmd. this will cun the on container
# CMD ["npm","run","dev"]
# #to build  the docker file "type docker build ."


# after separating development and production environment.

FROM  node:18
WORKDIR /app
COPY package.json .
# arg is used to make variables 
ARG NODE_ENV
RUN if [ "$NODE_ENV" = "development" ]; \
        then npm install; \
        else npm install --only=production; \
        fi
COPY . .
ENV PORT 3000
EXPOSE $PORT
CMD ["node","index.js"]