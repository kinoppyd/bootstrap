FROM fluent/fluentd:v1.3-onbuild

RUN apk add --update --virtual .build-deps sudo build-base ruby-dev \
    && sudo gem install fluent-plugin-influxdb \
    && sudo gem sources --clear-all \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/* /home/fluent/.gem/ruby/2.5.0/cache/*.gem

RUN mkdir -p /fluentd/etc/certs/
COPY fluentd.key /fluentd/etc/certs/
COPY fluentd.crt /fluentd/etc/certs/
RUN chmod 700 /fluentd/etc/certs/ 
RUN chmod 400 /fluentd/etc/certs/fluentd.key
