FROM mhart/alpine-node:12 AS builder
WORKDIR /app
COPY . .
RUN yarn install
RUN yarn build

FROM mhart/alpine-node:12
WORKDIR /app
COPY --from=builder /app/build .
RUN yarn global add serve@11
CMD ["serve", "-p", "80", "-s", "."]
