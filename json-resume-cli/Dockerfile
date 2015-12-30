FROM alpine

RUN apk add --update nodejs
RUN npm install -g resume-cli

WORKDIR /home
ENTRYPOINT ["resume", "export"]
