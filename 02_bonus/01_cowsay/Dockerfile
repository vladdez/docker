# docker build -t 01_cowsay .
# docker run -it 01_cowsay

FROM debian:latest

RUN apt-get update && \
	apt-get install -y cowsay fortune lolcat

ENTRYPOINT usr/games/fortune | usr/games/cowsay | usr/games/lolcat 
