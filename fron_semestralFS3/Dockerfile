# Etapa 1: Build (Compila el código de React/Vite)
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa 2: Runtime (Servidor Nginx súper liviano)
FROM nginx:alpine
# Copiamos los archivos compilados de la etapa anterior
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
EXPOSE 9090