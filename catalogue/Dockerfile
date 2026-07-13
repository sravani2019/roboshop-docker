FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install



FROM node:20.20.2-alpine3.22
WORKDIR /app

EXPOSE 8080
ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
    MONGO="true" 
#addgroup -S appgroup && adduser -S -G appgroup appuser
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop
RUN chown -R roboshop:roboshop /app
COPY --from=builder /app /app
USER roboshop
CMD ["node", "server.js"]


# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
#     MONGO="true" 
# CMD ["node", "server.js"]