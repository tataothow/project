# Use an official Node runtime as a parent image
FROM node:14-alpine
# Set the working directory in the container
WORKDIR /frontend
# Copy package.json and package-lock.json
COPY  package.json  package-lock.json .
# Install app dependencies
RUN npm install 
# Copy the current directory contents into the container
COPY . .
# Build the app
RUN npm start
# Make port 3000 available to the world outside this container
EXPOSE 3000

# Define environment variable
ENV PORT=3000

# Run the app when the container launches
CMD  ["npm", "start"]
