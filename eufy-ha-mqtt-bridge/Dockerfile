ARG BUILD_FROM
FROM $BUILD_FROM

ARG VERSION=0.2.13

RUN apk add --no-cache nodejs npm make g++ sqlite

# add source and unpack
ADD "https://github.com/ryaowe/eufy-ha-mqtt-bridge/releases/download/t8201/eufy-ha-mqtt-bridge.tar.gz" /src.tar.gz
RUN mkdir /app && tar xvfz /src.tar.gz -C /app --strip-components=1

# install all (and json2yaml for cofiguration parsing)
WORKDIR /app
RUN npm install && npm install -g json2yaml && echo ${VERSION} > /version

COPY run.sh /
RUN chmod a+x /run.sh
CMD [ "/run.sh" ]
