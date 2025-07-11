# Stage 1: Build the application
FROM node:20-alpine AS build

# Set working directory
WORKDIR /app

# Install dependencies separately for caching
COPY package*.json ./
RUN npm install

# Copy application code
COPY . .


# Stage 2: Run the application
FROM node:20-alpine



# Set working directory
WORKDIR /app

# Install Medusa CLI globally
RUN npm install -g @medusajs/medusa-cli

# Copy built application from previous stage
COPY --from=build /app .

# Expose Medusa port
EXPOSE 9000

# Start the app: run migrations and start server
CMD ["sh", "-c", "medusa migrations run && npm run start"]

