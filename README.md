# Quasar Plugin MS SQL Server [![Discord](https://img.shields.io/discord/373302030460125185.svg?logo=discord)](https://discord.gg/pSSqJrr)

## Usage

## Datasource

The MS SQL Server datasource plugin enables Quasar to load data from MS SQL Server. Most native column types are supported with the notable exception of `BINARY` variants.

This plugin also enables connection to Azure SQL Database (Microsoft's hosted SQL Server).

### Datasource Configuration

JSON configuration required to construct a MS SQL Server datasource.

```
{
  "connection": <connection-configuration>
}
```

* `connection`: A [connection configuration](#connection-configuration) object.


## Connection Configuration

JSON configurating describing how to connect to MS SQL Server.

```
{
  "jdbcUrl": String
  [, "maxConcurrency": Number]
  [, "maxLifetimeSecs": Number]
}
```

* `jdbcUrl`: a MS SQL Server [connection string](https://docs.microsoft.com/en-us/sql/connect/jdbc/building-the-connection-url?view=sql-server-ver15). Note that any connection parameter values containing URI [reserved characters](https://tools.ietf.org/html/rfc3986#section-2.2) must be [percent encoded](https://tools.ietf.org/html/rfc3986#section-2.1) to avoid ambiguity.
* `maxConcurrency` (optional): the maximum number of simultaneous connections to the database (default: 8)
* `maxLifetimeSecs` (optional): the maximum lifetime, in seconds, of idle connections. If your database or infrastructure imposes any limit on idle connections, make sure to set this value to at most a few seconds less than the limit (default: 300 seconds)

## Testing
Run the MS SQL Server docker image like so:
```
$ docker-compose up -d mssql
```
If you ever need to start the image without using docker-compose, do it like so:
```
$ sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
$ sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong@Passw0rd>" -p 1433:1433 --name sql1 -h sql1 -d mcr.microsoft.com/mssql/server:2019-latest
```
