FROM gcc:latest
ADD ./sqlite /usr/src/
COPY . /usr/src/sqlite
WORKDIR /usr/src/sqlite

RUN apt-get update && apt-get -y install cmake make

RUN cmake -S .

CMD ["make"]