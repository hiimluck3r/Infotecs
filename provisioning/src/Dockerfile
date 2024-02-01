FROM gcc:latest
COPY ../src /usr/src/sqlite
WORKDIR /usr/src/sqlite
RUN cmake -S .

ADD ./docker-out /usr/src/sqlite

CMD ["make"]