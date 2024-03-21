#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

# Install the latest version of font libraries
RUN apt update &&\
         apt install -y libc6 libicu-dev libfontconfig1
 
# (Optional step) Install the ttf-mscorefonts-installer package
# to use Microsoft TrueType core fonts in the application
RUN echo "deb http://ftp.debian.org/debian/ bullseye contrib" >> /etc/apt/sources.list
RUN apt update
RUN apt install -y ttf-mscorefonts-installer

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src

# Specify your DevExpress NuGet Feed URL as the package source
RUN dotnet nuget add source https://nuget.devexpress.com/{your-authorization-key}/api

# Copy the project file
COPY ["pdf-signature-validator/pdf-signature-validator.csproj", "pdf-signature-validator/"]

RUN dotnet restore "pdf-signature-validator/pdf-signature-validator.csproj"
COPY . .
WORKDIR "/src/pdf-signature-validator"
RUN dotnet build "pdf-signature-validator.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "pdf-signature-validator.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "pdf-signature-validator.dll"]