# Stage 1: Build the Angular app
FROM node:14 AS build

WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci --legacy-peer-deps

# Copy the rest of the application code
COPY . .

# Build the Angular app
RUN npm run build -- --prod

# Stage 2: Serve the app with Nginx
FROM nginx:alpine

# Copy build files to Nginx
COPY --from=build /app/dist/angularapp /usr/share/nginx/html

# Expose port 80
EXPOSE 80
