FROM node:14 AS builder
WORKDIR /home/visualdl
COPY . .
ENV SCOPE server
RUN ["./scripts/install.sh"]
RUN ["./scripts/build.sh"]

FROM node:14-alpine
WORKDIR /home/visualdl
COPY --from=builder /home/visualdl/output/server.tar.gz /tmp
RUN ["tar", "zxf", "/tmp/server.tar.gz"]
ENV NODE_ENV production
RUN ["yarn", "install", "--no-lockfile"]
ENTRYPOINT ["yarn", "start"]
