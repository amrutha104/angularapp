# Stage 1: Build the Angular app
FROM node:18 AS build

WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Angular app
RUN npm run build -- --prod

# Stage 2: Serve the app with Nginx
FROM nginx:alpine

COPY --from=build /app/dist/your-angular-project /usr/share/nginx/html

# Expose port 80
EXPOSE 80
