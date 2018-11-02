###
# Build
### 

FROM node:alpine as build
WORKDIR /apps

COPY package.json .
RUN npm install  
COPY . .
RUN npm run build

###
# Run
###

FROM nginx:alpine
EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /apps/build /usr/share/nginx/html