# Usa uma imagem do Node.js para construção do frontend
FROM node:20 AS build
WORKDIR /app

# Copia os arquivos do projeto
COPY ./app/package.json ./
COPY ./app/package-lock.json ./
RUN npm install

# Copia o restante dos arquivos e constrói o frontend
COPY ./app/ ./
RUN npm run build

# Serve os arquivos usando Nginx
FROM nginx:1.25
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 5001
CMD ["nginx", "-g", "daemon off;"]