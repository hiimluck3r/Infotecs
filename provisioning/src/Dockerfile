FROM gcc:latest

COPY . /var/sqlite/
WORKDIR /var/sqlite/

RUN apt-get update && apt-get -y install cmake

RUN cmake -S .
CMD ["make"]