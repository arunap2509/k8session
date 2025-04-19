FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY "Helper.csproj" .
RUN dotnet restore "Helper.csproj"
COPY . .
RUN dotnet build "Helper.csproj" -c Release -o /app/build
RUN dotnet publish "Helper.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0
EXPOSE 8080
WORKDIR /app
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "Helper.dll"]
