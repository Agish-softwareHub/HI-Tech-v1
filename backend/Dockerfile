# Use Node base image
FROM node:18

# Set working directory
WORKDIR /app

# Install dependencies
COPY backend/package.json backend/yarn.lock ./
RUN corepack enable && yarn install

# Copy backend code
COPY backend .

# Build and setup DB (optional: remove if you run DB manually)
RUN yarn medusa migrations:run
RUN yarn run seed
RUN yarn medusa user -e admin@test.com -p supersecret -i admin

# Expose Medusa port
EXPOSE 9000

# Start Medusa
CMD ["yarn", "start"]
