FROM node:20.10.0 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build

# FROM node:22-alpine
# WORKDIR /app
# COPY --from=build /app ./
# EXPOSE 5174
# CMD ["npm", "run", "dev", "--", "--host"]

# Stage 2: Serve React Application using Nginx
FROM nginx:alpine

# Copy the built React application to the Nginx server directory
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
# Expose port 80 to the outside world
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]