# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build

LABEL mantainer="Deyvisson Eduardo deyvissoneduardo22@gmail.com"

WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./

RUN dotnet restore

# copy everything else and build app
COPY . ./

RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:5.0

LABEL mantainer="Deyvisson Eduardo deyvissoneduardo22@gmail.com"

WORKDIR /app

COPY --from=build /app ./

EXPOSE 80

ENTRYPOINT ["dotnet", "ConversaoPeso.Web.dll"]