# docker build -t 00_invaders .
# docker run -it 00_invaders 

FROM debian:latest

RUN apt-get update && \
	apt-get install -y ninvaders

ENTRYPOINT usr/games/ninvaders
