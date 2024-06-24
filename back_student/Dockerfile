FROM node:11-alpine

RUN mkdir -p /usr/src/app/back

WORKDIR /usr/src/app/back

COPY . .

RUN yarn install


EXPOSE 3000
CMD ["yarn", "migration:start"]
CMD ["yarn", "start"]
