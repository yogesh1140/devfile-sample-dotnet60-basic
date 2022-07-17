# FROM registry.access.redhat.com/ubi8/dotnet-60:6.0 as builder
FROM mcr.microsoft.com/dotnet/sdk as builder
WORKDIR /opt/app-root/src
COPY --chown=1001 . .
RUN dotnet publish -c Release


# FROM registry.access.redhat.com/ubi8/dotnet-60:6.0
FROM mcr.microsoft.com/dotnet/runtime:6.0
EXPOSE 8081
ENV ASPNETCORE_URLS=http://*:8081
COPY --from=builder /opt/app-root/src/bin /opt/app-root/src/bin
WORKDIR /opt/app-root/src/bin/Release/net6.0/publish
CMD ["dotnet", "app.dll"]
