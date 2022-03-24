#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

# This stage is used for VS debugging on Docker
FROM mcr.microsoft.com/dotnet/aspnet:3.1-alpine AS base
ENV ASPNETCORE_URLS=https://+:5001;http://+:5000
WORKDIR /app
EXPOSE 5000
EXPOSE 5001

FROM mcr.microsoft.com/dotnet/sdk:3.1-alpine AS build
# RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
# RUN apt install -y nodejs
WORKDIR /src
COPY ["src/Koobits.DailyChallenge.Api/Koobits.DailyChallenge.Api.csproj", "src/Koobits.DailyChallenge.Api/"]
COPY ["src/Koobits.DailyChallenge.Application/Koobits.DailyChallenge.Application.csproj", "src/Koobits.DailyChallenge.Application/"]
COPY ["src/Koobits.DailyChallenge.Domain/Koobits.DailyChallenge.Domain.csproj", "src/Koobits.DailyChallenge.Domain/"]
COPY ["src/Koobits.DailyChallenge.Infrastructure/Koobits.DailyChallenge.Infrastructure.csproj", "src/Koobits.DailyChallenge.Infrastructure/"]
RUN dotnet restore "src/Koobits.DailyChallenge.Api/Koobits.DailyChallenge.Api.csproj"
COPY . .
WORKDIR "/src/src/Koobits.DailyChallenge.Api"
RUN dotnet build "Koobits.DailyChallenge.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Koobits.DailyChallenge.Api.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Koobits.DailyChallenge.Api.dll"]
