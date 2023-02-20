FROM node:19-alpine

RUN apk add --no-cache git
RUN npm i -g --save @vue/cli

WORKDIR /src

CMD ["vue", "create", "vue"]