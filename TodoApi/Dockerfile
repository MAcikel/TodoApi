FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS build-env
WORKDIR /app
COPY . .

RUN dotnet restore
RUN dotnet build -c Release -o /out
RUN dotnet publish -c Release -o /out

# Runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine
WORKDIR /app
COPY --from=build-env /out .
ENTRYPOINT ["dotnet", "TodoApi.dll"]
