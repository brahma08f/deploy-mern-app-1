# Step 1: Use an official Node.js image to build the frontend
FROM node:14 AS build

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy the package.json and package-lock.json to install dependencies
COPY package*.json ./

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the frontend code
COPY . .

# Step 6: Build the frontend for production
RUN npm run build

# Step 7: Use a lightweight web server to serve the built frontend (e.g., Nginx)
FROM nginx:alpine

# Step 8: Copy the build output to the Nginx server's public directory
COPY --from=build /app/build /usr/share/nginx/html

# Step 9: Expose the port the app will run on
EXPOSE 80

# Step 10: Start Nginx to serve the app
CMD ["nginx", "-g", "daemon off;"]
