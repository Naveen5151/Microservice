FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

# Build Stage
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
RUN pwd && ls
COPY ["Sample1/Sample1.csproj" , "Sample1/"]
RUN dotnet restore "Sample1/Sample1.csproj"
