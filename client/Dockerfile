# Prepare for Production
FROM node:alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
RUN npm audit fix --force
COPY . .
RUN npm run build

# Set Production
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
