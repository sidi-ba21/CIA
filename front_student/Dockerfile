FROM mhart/alpine-node:11 AS builder

RUN mkdir -p /usr/src/app/front
WORKDIR /usr/src/app/front
COPY front_student/ ./
COPY front_student/package.json front_student/yarn.lock ./
RUN yarn install
RUN yarn build
# RUN ls -lR

FROM nginx
WORKDIR /usr/src/app/front
COPY --from=builder /usr/src/app/front /usr/share/nginx/html