# for production process
FROM node:20.11-alpine as builder

WORKDIR /app
COPY  ./package.json . 
RUN npm install
COPY  . .
RUN  npm run build

FROM nginx
#  looking for port 3000
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy to nginx file response for localhost: 3000
# from build process and place to nginx html
COPY --from=builder /app/build /usr/share/nginx/html