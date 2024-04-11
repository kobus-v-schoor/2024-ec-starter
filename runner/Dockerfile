# syntax=docker/dockerfile:1-labs

# prevent dotnet telemetry
ARG DOTNET_CLI_TELEMETRY_OPTOUT=1

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

# retrieve the repo
ARG TAG=v2024.0.1
WORKDIR /app
ADD https://github.com/EntelectChallenge/2024-Sproutopia.git#${TAG} .

# build the runner
WORKDIR /app/Sproutopia
RUN dotnet restore
RUN dotnet publish --configuration Release --output ./publish

# set up the run image
FROM mcr.microsoft.com/dotnet/aspnet:8.0

# install some extra tools
RUN apt update && apt install -y vim make

# copy the built app
WORKDIR /app
COPY --from=build /app/Sproutopia/publish .

# switch to the runner directory
WORKDIR /runner

EXPOSE 5000

CMD ["dotnet", "/app/Sproutopia.dll"]
