FROM alpine:20200917

#Fix pb with terminal not setted
ENV TERM=xterm

#Install rtorrent & curl
RUN apk add --no-cache rtorrent
RUN apk add --no-cache curl
RUN apk add --no-cache dtach
#RUN apk add --no-cache nano

#Create directory and move into it
WORKDIR /root

#Download rtorrent config template and store it in /root/.rtorrent.rc
RUN curl -Ls "https://raw.githubusercontent.com/wiki/rakshasa/rtorrent/CONFIG-Template.md" | grep -A9999 '^######' | grep -B9999 '^### END' | sed -re "s:/home/USERNAME:$HOME:" >~/.rtorrent.rc

#Copy start rtorrent template and make it runable
WORKDIR /root/rtorrent
COPY templates/start_minimal ./start 
RUN chmod a+x ./start
CMD ./start


HEALTHCHECK --interval=10s --timeout=3s CMD pgrep -x rtorrent || exit 1

EXPOSE 5000