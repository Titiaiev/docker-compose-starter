FROM node:8.12-alpine
EXPOSE 8080
COPY package.json /app/
RUN cd /app && \
    npm install --quiet --production
COPY . /app
WORKDIR /app

CMD npm run start
