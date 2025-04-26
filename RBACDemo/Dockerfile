FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY "RBACDemo.csproj" .
RUN dotnet restore "RBACDemo.csproj"
COPY . .
RUN dotnet build "RBACDemo.csproj" -c Release -o /app/build
RUN dotnet publish "RBACDemo.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0
EXPOSE 8080
WORKDIR /app
ENV ASPNETCORE_URLS=http://0.0.0.0:8080

COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "RBACDemo.dll"]