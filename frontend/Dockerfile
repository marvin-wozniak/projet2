FROM node:lts-alpine as build

WORKDIR /app

COPY package*.json ./

RUN npm install --legacy-peer-deps

COPY . . 

RUN npm run build-only

FROM nginx:stable-alpine

COPY --from=build /app/dist /usr/share/nginx/html 

EXPOSE 80

CMD ["nginx", "-g", "deamon off;"]