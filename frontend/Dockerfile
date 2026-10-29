# Build
FROM node:24-alpine AS build
WORKDIR /app
COPY package*.json ./
# npm ci installs the lockfile's @angular/cli; a global install would pull whatever is latest.
RUN npm ci
COPY . .
RUN npm run build:prod

# Host
FROM nginx:latest
COPY --from=build app/dist/my-angular-app/browser /usr/share/nginx/html
EXPOSE 80
