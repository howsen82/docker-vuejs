FROM node:19 as dev
WORKDIR /src

RUN chown node:node /src

USER node
COPY package.json /src/
RUN npm i

COPY server.js routes.js dev-entrypoint.sh /src/

ENV TZ="Asia/Kuala_Lumpur"

ENTRYPOINT [ "/src/dev-entrypoint.sh" ]

CMD [ "npx", "nodemon", "server.js" ]

FROM node:19-alpine
WORKDIR /src
RUN chown node:node /src
USER node
COPY package.json /src/
RUN npm i --production
COPY server.js routes.js health.js /src/
HEALTHCHECK --interval=10s --timeout=3s CMD node /src/health.js || exit 1

EXPOSE 3000

ENV TZ="Asia/Kuala_Lumpur"
CMD [ "npm", "start" ]