FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install



FROM node:20.20.2-alpine3.22
WORKDIR /app
COPY --from=builder /app /app
EXPOSE 8080
ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
    MONGO="true" 
CMD ["node", "server.js"]


# FROM node:20.20.2-alpine3.22 AS builder
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO_URL="mongodb://mongodb:27017/catalogue" \
#     MONGO="true" 
# CMD ["node", "server.js"]