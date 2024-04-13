#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
EXPOSE 6969
EXPOSE 6970

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["MichaelSoft Aruze Dev opps/MichaelSoft Aruze Dev opps.csproj", "MichaelSoft Aruze Dev opps/"]
RUN dotnet restore "./MichaelSoft Aruze Dev opps/MichaelSoft Aruze Dev opps.csproj"
COPY . .
WORKDIR "/src/MichaelSoft Aruze Dev opps"
RUN dotnet build "./MichaelSoft Aruze Dev opps.csproj" -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "./MichaelSoft Aruze Dev opps.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "MichaelSoft Aruze Dev opps.dll"]