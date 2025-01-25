# Use a lightweight Node.js image based on Alpine
FROM node:18.12.1-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package.json package-lock.json ./

# Install dependencies (no separate production dependencies)
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose the application port
EXPOSE 8080

# Use a non-root user for security (optional)
RUN adduser -D appuser
USER appuser

# Start the application
CMD ["npm", "start"]
