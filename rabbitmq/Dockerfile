ARG RABBITMQ_VERSION=alpine
FROM rabbitmq:${RABBITMQ_VERSION}

LABEL maintainer="Mahmoud Zalt <mahmoud@zalt.me>"

RUN rabbitmq-plugins enable --offline rabbitmq_management

EXPOSE 4369 5671 5672 15671 15672 25672