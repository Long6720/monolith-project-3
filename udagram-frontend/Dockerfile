### Build
FROM beevelop/ionic:v2021.06.1 AS ionic
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm install --omit=optional
## Bundle app source
COPY . .
# Set the NODE_OPTIONS environment variable and run the build
RUN ionic build
### Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html