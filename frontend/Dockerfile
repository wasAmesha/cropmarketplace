# Stage 1: Build the React app
FROM node:14 AS build

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Stage 2: Serve the app using Nginx
FROM nginx:alpine

# Copy build artifacts from the build stage
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Copy custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]


# # Use the official Node.js image as a base image
# FROM node:14

# # Set the working directory
# WORKDIR /app

# # Copy package.json and package-lock.json
# COPY package*.json ./

# # Install dependencies
# RUN npm install

# # Copy the rest of the application files
# COPY . .

# # Build the React app for production
# RUN npm run build

# # Install a simple HTTP server to serve the static files
# RUN npm install -g serve

# # Expose the port the app runs on
# EXPOSE 3000

# # Serve the React app
# CMD ["serve", "-s", "build"]
