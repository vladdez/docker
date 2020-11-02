# docker build -t ex00 .
# docker run --interactive --tty --rm ex00

FROM alpine
RUN apk update && apk upgrade
RUN apk add vim 
ENTRYPOINT vim 