FROM node:20-alpine

WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --omit=dev

# Copy rest of the code
COPY . .

EXPOSE 5000
CMD ["node", "server.js"]


