#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/runtime:3.1-buster-slim AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["Hello/Hello.csproj", "Hello/"]
RUN dotnet restore "Hello/Hello.csproj"
COPY . .
WORKDIR "/src/Hello"
RUN dotnet build "Hello.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Hello.csproj" -c Release -o /app/publish


FROM base AS final
WORKDIR /app
ENTRYPOINT ["dotnet",  "Hello.dll"] 