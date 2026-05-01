# ---------- Stage 1: Dependencies ----------
FROM node:20 AS deps

WORKDIR /app

# Only copy package files first (better caching)
COPY package*.json ./

# Use npm ci for reproducible + faster installs
RUN npm ci


# ---------- Stage 2: Runtime ----------
FROM node:20 AS runner

WORKDIR /app

# Copy node_modules from deps stage
COPY --from=deps /app/node_modules ./node_modules

# Copy the rest of your source code
COPY . .

EXPOSE 3000

CMD ["npm", "start"]