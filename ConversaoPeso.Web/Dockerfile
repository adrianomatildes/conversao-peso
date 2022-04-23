FROM mcr.microsoft.com/dotnet/sdk:5.0 AS buid
WORKDIR /app
RUN dotnet --version

# Copiar csproj e restaurar dependecias
COPY *.csproj ./
COPY . .
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=buid /app/out .
ENTRYPOINT [ "dotnet", "ConversaoPeso.Web.dll" ]