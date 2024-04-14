## Note2: Install SQLServer 

### 1. Download Docker
https://www.docker.com/products/docker-desktop/

### 2. Open Docker.dmg

### 3. Update Setting
> Docker > Setting > Advance > [ ] automaticly check configuration.

### 4. Download SQL Server Image
by https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker in terminal run:
```
sudo docker pull mcr.microsoft.com/mssql/server:2022-latest
```
### 5. Install SQL Server Image
by https://learn.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker in terminal run:
```
sudo docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong@Passw0rd>" \
   -p 1433:1433 --name sql1 --hostname sql1 \
   -d \
   mcr.microsoft.com/mssql/server:2022-latest
```
### 6. Download Azure Data Studio
A modern open-source, cross-platform hybrid data analytics tool designed to simplify the data landscape.
https://azure.microsoft.com/en-us/products/data-studio

### 7. Connect Server
Azure Data Studio > Create a Connection >
```
  server: localhost
  authentication type: SQL login
  user name: SA
  password: <YourStrong@Passw0rd>
```
Connect!
