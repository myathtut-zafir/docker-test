FROM node:19.6-alpine

WORKDIR /usr/src/app

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm\
npm set cache /usr/src/app/.npm && \
npm ci --only=production

ENV NODE_ENV production

RUN npm ci --only=production

USER node

COPY --chown=node:node ./src .

EXPOSE 3000

CMD [ "npm","index.js" ]
