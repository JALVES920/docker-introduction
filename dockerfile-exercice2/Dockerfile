FROM node:18-alpine
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build && \
    npm install -g serve && \
    rm -fr node_modules
EXPOSE 3000
CMD [ "serve", "-s", "dist" ]