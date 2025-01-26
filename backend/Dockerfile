# Utiliza imagem oficial do SDK .NET para build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app

# Copia os arquivos do projeto e restaura dependências
# COPY ./app/*.csproj ./
RUN dotnet restore

# Copia todo o código e publica o aplicativo
# COPY ./app/ ./
RUN dotnet publish -c Release -o out

# Runtime image para execução da aplicação
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app/out .

# Expõe as portas do aplicativo
EXPOSE 5000 5001
ENTRYPOINT ["dotnet", "backend.dll"]