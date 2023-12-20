FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
# Copy everything
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["Sample1/Sample1.csproj", "Sample1/"]
RUN dotnet restore "Sample1/Sample1.csproj"
WORKDIR "/src/Sample1"
COPY . .
RUN dotnet build "Sample1.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Sample1.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM  base AS final 
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Sample1.dll"]
