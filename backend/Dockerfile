#Dockerfile dla backendu
#Wykorzystujemy minimalny obraz systemu Linux (Alpine)
FROM alpine
#Instalacja narzędzia curl do testów łączności międzyserwisowej
RUN apk add --no-cache curl
#Wypisanie statusu i zapętlenie procesu, aby kontener pozostał aktywny
CMD ["sh", "-c", "echo 'Backend service is running...' && sleep infinity"]

FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish


FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 80
# Nazwa pliku.dllmusiodpowiadaćnazwieTwojegoprojektu
ENTRYPOINT ["dotnet", "CloudBackend.dll"]