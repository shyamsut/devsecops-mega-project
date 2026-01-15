# ---------- STAGE 1: DEPENDENCIES ----------
FROM node:21 AS backend-builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# ❌ NO TESTS HERE

# ---------- STAGE 2: RUNTIME ----------
FROM node:21-slim

WORKDIR /app

COPY --from=backend-builder /app .

COPY .env.docker .env

EXPOSE 8080

CMD ["npm", "start"]
