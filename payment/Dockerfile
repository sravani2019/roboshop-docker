FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
# COPY payment.ini .
# COPY *.py .
COPY requirements.txt .
RUN apk add --no-cache --virtual .build-deps gcc musl-dev linux-headers python3-dev\
    && pip3 install --prefix=/install -r requirements.txt \
    && apk del .build-deps

FROM python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --chown=roboshop:roboshop --from=builder /install /usr/local
COPY payment.ini *.py requirements.txt .
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]


# FROM python:3.9
# WORKDIR /app
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt 
# EXPOSE 8080
# CMD ["uwsgi", "--ini", "payment.ini"]