# Deployment Guide (Azure)
<br>

## Resources
- Resource Group: myspace-rg
- App Service: myspace-core-api
- App Service: musicspace-api
- PostgreSQL: myspace-db
<br>

## Core Backend
```
cd Core/backend
az webapp up --name myspace-core-api --runtime "node|18-lts"
```
<br>

## MusicSpace Backend
```
cd MusicSpace/backend
az webapp up --name musicspace-api --runtime "node|18-lts"
```