FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY Bob/*.csproj ./Bob/
RUN dotnet restore

# copy everything else and build app
COPY . .
WORKDIR /app/Bob
RUN dotnet build

WORKDIR /app/Bob/bin/Debug
ENTRYPOINT ["Bob.exe"]
