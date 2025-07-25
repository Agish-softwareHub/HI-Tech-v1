FROM node:18

WORKDIR /app

COPY storefront/package.json storefront/yarn.lock ./
RUN corepack enable && yarn install

COPY storefront .

EXPOSE 3000
CMD ["yarn", "start"]
