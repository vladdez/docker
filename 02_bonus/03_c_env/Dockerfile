# docker build -t 03_c_env .
# docker run -it 03_c_env

FROM ubuntu

ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update && \
	apt-get install -y build-essential git vim valgrind

CMD ["bash"]
