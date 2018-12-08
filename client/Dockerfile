FROM node:alpine as builder
WORKDIR '/app'
COPY package*.json ./
RUN npm install 
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
# copy over the config
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy over assets from build
COPY --from=builder /app/build /usr/share/nginx/html