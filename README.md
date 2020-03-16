# openapi-audit-engine

Make your API definition (Open API Standard) clean.  
<img width="1440" alt="Capture d’écran 2020-03-17 à 00 01 40" src="https://user-images.githubusercontent.com/12186878/76806883-e75b1f80-67e2-11ea-91bf-cc1d5a51e405.png">  

Based on [stoplightio/spectral](https://github.com/stoplightio/spectral)

## UI
The UI is handled by [RTabary/openapi-audit-engine-front](https://github.com/RTabary/openapi-audit-engine-front)

## API
The backend API is handled by [RTabary/openapi-audit-engine-back](https://github.com/RTabary/openapi-audit-engine-back)

## Run application (Docker)

```bash
$ docker-compose pull
$ docker-compose -f "docker-compose.yml" up -d --build
```
The UI is available at http://localhost:4200  
The API is available at http://localhost:3000

## Use your own rules

As previously mentionned, this project is based on [stoplightio/spectral](https://stoplight.io/p/docs/gh/stoplightio/spectral) which allows you to create your own custom rules.  
Simply bind the folder containing your own rules to the container:

```yaml
version: '2.0'
services:
  front:
    image: roms/openapi-audit-engine-front:latest
    ports:
    - "4200:4200"
  back:
    image: roms/openapi-audit-engine-back:latest
    volumes: 
    - "/path/to/local/spectral/conf:/usr/src/app/dist/assets:ro"
    ports: 
    - "3000:3000"
```

