
FROM node:12.11.1 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build -- --outputPath=./dist/out --configuration production

# Stage : run
FROM nginx
COPY --from=build /app/dist/out/ /usr/share/nginx/html
COPY /nginx-custom.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

ENTRYPOINT ["nginx","-g","daemon off;"]