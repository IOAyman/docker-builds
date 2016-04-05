FROM debian:jessie

RUN apt-get update && apt-get install -y fortunes cowsay \
	&& rm -rf /var/lib/apt/lists/* 
ENV PATH $PATH:/usr/games
ADD bba.cow /usr/share/cowsay/cows/bba.cow

CMD fortune -a | cowsay -f bba
