FROM mcr.microsoft.com/dotnet/core/sdk:3.0 AS build

COPY /src /src

RUN dotnet restore /src/ContosoUniversity.sln

WORKDIR /src

RUN echo 'TEST' \
    && dotnet publish -c Release -o /output

FROM mcr.microsoft.com/dotnet/core/aspnet:3.0


COPY --from=build /output ./

EXPOSE 80

#ENTRYPOINT [ "/opt/entrypoint.sh" ]
ENTRYPOINT [ "dotnet", "./ContosoUniversity.dll" ]
