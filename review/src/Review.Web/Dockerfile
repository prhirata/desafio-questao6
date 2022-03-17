# Base image (Build)
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-img
WORKDIR /app
COPY *.csproj ./
RUN dotnet restore
COPY . ./
RUN dotnet publish -c Release -o pub

# Runtime image
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build-img /app/pub .
ENTRYPOINT ["dotnet", "Review.Web.dll"]