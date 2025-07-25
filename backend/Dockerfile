# Use Node base image
FROM node:18

# Enable Corepack (for Yarn 4)
RUN corepack enable

# Set working directory
WORKDIR /app

# Copy Yarn config + package metadata
COPY . ./yarn.lock . ./package.json . ./.yarnrc.yml ./

# Install dependencies using Yarn 4
RUN yarn install

# Copy the rest of the backend code
COPY . .

# Run Medusa setup
RUN yarn medusa db:migrate
RUN yarn run seed
RUN yarn medusa user -e admin@test.com -p supersecret -i admin

# Expose backend port
EXPOSE 9000

# Start server
CMD ["yarn", "start"]
