#Use official node runtime as the base image
FROM node:22-alpine AS build

#Create a working directory inside the container
WORKDIR /app

#Copy and install dependencies inside the container
COPY package.json  package-lock.json /app/
RUN npm i

#Copy the rest of the code inside the container
COPY . .

#Final stage with distroless base image
FROM gcr.io/distroless/base

COPY --from=build /app .

#Expose a port
EXPOSE 3001

#Run the application
CMD [ "npm", "start" ]