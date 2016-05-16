FROM fedora:23
MAINTAINER Ayman Nedjmeddine ( @IOAyman )

# HowTo run this image
# docker run -d --name=movies \
#            -e DISPLAY=$DISPLAY \
#            -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
#            ioayman/popcorntime

#RUN dnf check-update
RUN dnf install -y curl git nodejs npm

WORKDIR /cinema
RUN git clone https://github.com/popcorn-official/popcorn-desktop.git . && \
    git submodule init
    #git submodule update
RUN curl -L popcorntime.sh/package.json -o package.json && \
    curl -L popcorntime.sh/torrent_collection.js -o torrent_collection.js && \
    curl -L popcorntime.sh/ysubs.js -o ysubs.js
RUN npm install -g bower gulp grunt-cli jit-grunt
RUN npm install
RUN bower --allow-root install

VOLUME ["/streaming"]
RUN cat src/app/settings.js | sed s/'os.tmpDir(), Settings.projectName'/"'\/streaming'"/ > src/app/settings.new.js

ENTRYPOINT ["/bin/npm"]
CMD ["start"]
