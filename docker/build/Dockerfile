FROM openjdk:8

LABEL maintainer "MAIF <oss@maif.fr>"

RUN groupadd -g 999 otoroshi && useradd -r -u 999 -g otoroshi otoroshi

RUN mkdir -p /usr/app

WORKDIR /usr/app

COPY . /usr/app

RUN unzip ./otoroshi-dist.zip \
  && mv otoroshi-1.2.0-dev otoroshi \
  && chmod +x otoroshi/bin/otoroshi \
  && mkdir otoroshi/leveldb \
  && mkdir otoroshi/imports \
  && chown -R otoroshi:otoroshi /usr/app/otoroshi

VOLUME /usr/app/otoroshi/imports
VOLUME /usr/app/otoroshi/leveldb
VOLUME /usr/app/otoroshi/conf

ENTRYPOINT ["./entrypoint.sh"]

USER otoroshi

EXPOSE 8080

CMD [""]