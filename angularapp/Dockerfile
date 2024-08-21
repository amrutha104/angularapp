# Stage 1: Build the Angular app
FROM node:18 AS build

WORKDIR /app

# Console statement to indicate starting dependency installation
RUN echo "Starting npm install..."

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies with legacy peer deps option and log output
RUN echo "Installing dependencies..." && npm ci --legacy-peer-deps

# Console statement to confirm successful installation
RUN echo "Dependencies installed successfully."

# Copy the rest of the application code
COPY . .

# Console statement to indicate the start of the build process
RUN echo "Starting Angular build..."

# Build the Angular app
RUN npm run build -- --prod

# Console statement to confirm successful build
RUN echo "Angular app built successfully."

# Stage 2: Serve the app with Nginx
FROM nginx:alpine

# Console statement to indicate the start of the copy process
RUN echo "Copying build files to Nginx..."

COPY --from=build /app/dist/your-angular-project /usr/share/nginx/html

# Console statement to confirm the files are copied
RUN echo "Files copied successfully."

# Expose port 80
EXPOSE 80

# Final console statement to confirm the image is ready
RUN echo "Docker image built and ready to serve the Angular app."
