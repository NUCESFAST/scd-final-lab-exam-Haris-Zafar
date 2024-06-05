# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/20i1885_Client

# Copy package.json and package-lock.json files to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Build the React app
RUN npm run build

# Use an official nginx image to serve the build files
FROM nginx:alpine

# Copy the build files to the nginx html directory
COPY --from=0 /usr/src/app/build /usr/share/nginx/html

# Expose the port nginx is running on
EXPOSE 80

# Start nginx when the container starts
CMD ["nginx", "-g", "daemon off;"]
