# TO BUILD use:
#   docker build -t latrokles/dev-java .

# TO RUN use: 
#   docker run -it \
#          -v ~/workspace:/home/user/workspace \
#          -v ~/vim:/home/user/.vim \
#          --name dev-rust \
#          latrokles/dev-java

FROM latrokles/base-dev-env:latest
MAINTAINER latrokles@gmail.com

USER root
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" \
    | tee /etc/apt/sources.list.d/webupd8team-java.list
RUN echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" \
    | tee -a /etc/apt/sources.list.d/webupd8team-java.list

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886
RUN apt-get update
RUN apt-get install -y oracle-java8-installer

USER user
