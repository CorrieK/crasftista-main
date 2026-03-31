# Stage 1: Build the application
FROM node:20.11-bookworm-slim

WORKDIR /app

# Copy package.json and package-lock.json (or yarn.lock) first to leverage Docker cache
COPY package.json .
RUN npm install --production

# Copy the rest of the application code
COPY . .


# Expose the port the app runs on (default is often 3000 for Node.js apps)
EXPOSE 3000

# Define the command to run the application
CMD ["npm", "start"]
