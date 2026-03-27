#Multi stage docker build

#Build stage
FROM node:18-alpine AS builder

#Set Working directory
WORKDIR /app

#Copy dependencies
COPY package*.json ./

#Install dependencies
RUN npm ci

#Copy source code files
COPY . .

#Build the source code
RUN npm run build

#Deploy stage
FROM node:18-alpine

#Set Working directory
WORKDIR /app

#Copy built assets from the build stage
COPY --from=builder /app/dist ./dist

#Install simple http server
RUN npm install -g http-server

#Expose port
EXPOSE 8080

#Run the app
CMD ["http-server", "dist", "-p", "8080", "-c-1"]























