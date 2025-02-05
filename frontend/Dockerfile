# First Stage: Build
FROM node:latest AS frontend-builder

WORKDIR /app

COPY package*.json  /app

# Install dependencies without running lifecycle scripts
RUN npm install --upgrade npm

COPY . .
# Second Stage: Production
FROM node:alpine

WORKDIR /app

COPY --from=frontend-builder /app .

COPY .env.local .env.local

CMD ["npm", "run", "dev", "--", "--host"]
