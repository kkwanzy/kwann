FROM node:18-alpine AS build-step

WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:1.23.1-alpine
COPY --from=build-step /app/build /usr/share/nginx/html
EXPOSE 80