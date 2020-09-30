FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY Alice/*.csproj ./Alice/
RUN dotnet restore

# copy everything else and build app
COPY . .
WORKDIR /app/Alice
RUN dotnet build

WORKDIR /app/Alice/bin/Debug
ENTRYPOINT ["Alice.exe"]
