# 1. Base image
FROM node:22-alpine

# 2. Create app directory
WORKDIR /app

# 3. Copy package files first (for caching)
COPY package*.json ./

# 4. Install dependencies
RUN npm ci

# 5. Copy all source code
COPY . .

# 6. Generate Prisma client
RUN npx prisma generate

# 7. Build NestJS app
RUN npm run build

# 8. Expose backend port
EXPOSE 3000

# 9. Start application
CMD ["node", "dist/src/main.js"]