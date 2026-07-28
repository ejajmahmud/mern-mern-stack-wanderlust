# Stage 1: Backend Builder
FROM node:21 AS backend-builder

WORKDIR /app

# Copy project files
COPY . .

# Install dependencies
RUN npm install

# Ensure nodemon is executable
RUN chmod +x /app/node_modules/.bin/nodemon

# Stage 2: Backend Runtime
FROM node:21-slim

WORKDIR /app

# Copy the build artifacts from stage 1
COPY --from=backend-builder /app .

# Expose the application port
EXPOSE 5000

# Set the default command to use nodemon
CMD ["npx", "nodemon", "server.js"]
