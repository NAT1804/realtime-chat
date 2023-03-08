# Specify Node Version and Image
# Name Image development 
FROM node:16 AS development

# Specify working directory inside container
WORKDIR /workspace/api/src/app

# Copy package.json from host to inside container working directory
COPY package.json ./

# Copy yarn.lock from host to inside container working directory
COPY yarn.lock ./

# Install deps inside container
RUN yarn

# Bundle App Sources
COPY . .

RUN yarn build

EXPOSE 3000

# PRODUCTION
# Image for product
FROM node:16 AS production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

# Set workdir
WORKDIR /workspace/api/src/app

# Copy 
COPY --from=development /workspace/api/src/app/ .

EXPOSE 3000

# Run app
CMD [ "node", "dist/main" ]
