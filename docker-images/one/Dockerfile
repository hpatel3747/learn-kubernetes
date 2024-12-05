FROM        docker.io/redhat/ubi8
RUN         dnf install nginx -y
ENTRYPOINT  ["nginx", "-g", "daemon off;"]
EXPOSE      80