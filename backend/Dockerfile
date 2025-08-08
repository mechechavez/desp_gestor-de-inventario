# Dockerfile para la aplicación backend de Node.js
# Este Dockerfile está dividido en dos etapas: construcción y ejecución
# Etapa 1: Construcción
FROM node:18

WORKDIR /app

# Instalar dependencias
COPY package*.json ./
RUN npm install

# Copiar el código fuente
COPY . .

# Compilar TypeScript
RUN npm run build

# Limpiar dependencias de desarrollo después del build
RUN npm prune --omit=dev

# Puerto expuesto (cambia si usas otro)
EXPOSE 5000

# Comando de inicio correcto
CMD ["node", "dist/server.js"]
