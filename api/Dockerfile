FROM node:10-alpine
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
WORKDIR /home/node/app
COPY package*.json ./
RUN npm install --quiet
COPY . .
COPY --chown=node:node . .
RUN npm run build && \
    npm prune --production
USER node
EXPOSE 8080
CMD npm run start