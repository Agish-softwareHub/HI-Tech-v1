FROM node:18

WORKDIR /app

COPY package.json yarn.lock ./
RUN corepack enable && yarn install

COPY . .

RUN yarn medusa migrations:run
RUN yarn run seed
RUN yarn medusa user -e admin@test.com -p supersecret -i admin

EXPOSE 9000

CMD ["yarn", "start"]
