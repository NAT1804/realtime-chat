FROM node:16 as development

WORKDIR /workspace/fe/src/app

COPY package.json ./

COPY yarn.lock ./

RUN yarn

RUN npm i -g @angular/cli@15.2.0

COPY . .

RUN yarn build

EXPOSE 4200
