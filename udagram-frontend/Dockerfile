## Build
FROM beevelop/ionic:latest AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:1.23.1-alpine
#COPY www /usr/share/nginx/html
COPY /nginx-configs/ /etc/nginx/conf.d/
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html