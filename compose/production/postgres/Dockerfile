FROM postgres:12.3

COPY ./compose/production/postgres/maintenance /usr/local/bin/maintenance
RUN chmod +x /usr/local/bin/maintenance/*

RUN cp -r /usr/local/bin/maintenance/* /usr/local/bin \
    && rm -rf /usr/local/bin/maintenance
