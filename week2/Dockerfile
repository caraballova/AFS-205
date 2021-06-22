FROM alpine:latest 
# From instruction tells Docker which base you would like to use for your image
LABEL maintainer="Russ McKendrick <russ@mckendrick.io>"
# Label instruction can be used to add extra information to the image
# Maintainer adds a label that helps the end user of the image identify who is maintaining it.
LABEL description="This example Dockerfile installs NGINX."
# Description adds a brief description of what the image is
RUN apk add --update nginx && \
# Run instruction is where we interact with our image to install software and run scripts, commands, and other tasks.
    rm -rf /var/cache/apk/* && \
# removes any temp files to keep the size of our image to a min.
    mkdir -p /tmp/nginx/
# creates a folder with a path of /tmp/nginx so that NGINX will start correctly when you run the container: mkdir -p /tmp/nginx



COPY files/nginx.conf /etc/nginx/nginx.conf
COPY files/default.conf /etc/nginx/conf.d/default.conf
#Copying two files from the files folder on the host you are building your image on

ADD files/html.tar.gz /usr/share/nginx/
# adding a file called html.tar.gz, but you are not actually doing anything with the archive to uncompress it in our Dockerfile.

EXPOSE 80/tcp
# Expose instruction lets Docker know that when the image is executed, the port and protocol defined will be exposed at runtime.

ENTRYPOINT [“nginx”]
CMD [“-g”, “daemon off;”]
# What this means is that whenever we launch a container from our image, the NGINX binary is executed, which, as we have defined, is our entry point. Then, whatever we have as CMD is executed.