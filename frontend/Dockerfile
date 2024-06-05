FROM node:20.10.0 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build

FROM node:22-alpine
WORKDIR /app
COPY --from=build /app ./
CMD ["npm", "run", "dev", "--", "--host"]