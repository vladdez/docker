# docker build -t 02_greed .
# docker run -it 02_greed

FROM ubuntu

RUN apt-get update && \
	apt-get install -y greed

ENTRYPOINT usr/games/greed
