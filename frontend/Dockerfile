# Etapa 1: Construcción con Node
FROM node:20-alpine AS build

WORKDIR /app

# Instalar dependencias
COPY package*.json ./
RUN npm install

# Copiar el código y construir
COPY . .
RUN chmod -R 755 /app && npm run build

# Etapa 2: Servir con Nginx
FROM nginx:stable-alpine

# Eliminar configuración por defecto de Nginx
RUN rm /etc/nginx/conf.d/default.conf

# Copiar configuración personalizada
COPY nginx.conf /etc/nginx/conf.d

# Copiar build generado
COPY --from=build /app/dist /usr/share/nginx/html

# Puerto de Nginx
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
