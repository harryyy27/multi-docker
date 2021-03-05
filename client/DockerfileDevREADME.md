## SPECIFY image to use
FROM node:alpine

IF EACCES error occurs
## specify user
USER node

## set npm directory via env variable for global installations

ENV NPM_CONFIG_PREFIX='/home/node/.npm-global/bin

## set path / environment variable for npm

ENV PATH=$PATH:/home/node/.npm-global/bin

## set working directory

WORKDIR '/home/node'

## copy package.json whilst setting owner to node

COPY --chown=node:node package.json .

## install all npm packages

RUN npm install

## copy all other files in directory

COPY --chown=node:node .

## command to start up container

CMD ["npm","run","start"]
