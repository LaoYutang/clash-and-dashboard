FROM --platform=$TARGETPLATFORM dreamacro/clash:v1.16.0

ENV SERVER_PORT=8080
EXPOSE ${SERVER_PORT}

RUN apk update && apk add nginx

COPY ./dist/ /dashboard
COPY ./build/nginx.conf /etc/nginx
RUN sed -i "s/8080/$SERVER_PORT/g" /etc/nginx/nginx.conf
COPY ./build/start.sh /

ENTRYPOINT [ "sh", "/start.sh" ]
