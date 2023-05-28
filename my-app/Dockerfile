# Stage 1: Build the application
FROM node:18 as build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run-script build

# Stage 2: Serve the application
FROM node:18 as serve

WORKDIR /app

# Copy only the built application and server.js file from previous stage
COPY --from=build /app/build ./build
COPY server.js .

RUN npm install express

EXPOSE 3000

CMD [ "node", "server.js" ]