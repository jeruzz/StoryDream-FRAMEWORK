# StoryDream-FRAMEWORK - API Usage Guide

## Descripción
Este repositorio contiene la base de datos de conocimiento para el GPT generador de estructuras narrativas.

## Autenticación

### Personal Access Token
Usa el token generado:
```
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
```

### Headers requeridos
```json
{
  "Authorization": "Bearer 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",
  "Accept": "application/vnd.github+json",
  "X-GitHub-Api-Version": "2022-11-28"
}
```

## Endpoints de la API de GitHub

### 1. Obtener lista de archivos del repositorio
```
GET https://api.github.com/repos/jeruzz/StoryDream-FRAMEWORK/contents/
```

### 2. Obtener contenido de un archivo específico
```
GET https://api.github.com/repos/jeruzz/StoryDream-FRAMEWORK/contents/{path}
```
Ejemplo:
```
GET https://api.github.com/repos/jeruzz/StoryDream-FRAMEWORK/contents/templates/thriller.json
```

### 3. Leer archivos de base de datos
```
GET https://api.github.com/repos/jeruzz/StoryDream-FRAMEWORK/contents/database/{archivo}.json
```

## Estructura del Repositorio

```
StoryDream-FRAMEWORK/
├── README.md
├── API_USAGE.md
├── database/
│   ├── generos.json
│   ├── estructuras.json
│   ├── plot_twists.json
│   └── personajes.json
├── templates/
│   ├── novela.json
│   ├── pelicula.json
│   ├── microcuento.json
│   └── saga.json
└── ejemplos/
    ├── thriller_psicologico.json
    ├── drama_romantico.json
    └── accion_epica.json
```

## Ejemplo de uso en ChatGPT Actions

### Schema OpenAPI para ChatGPT
```yaml
openapi: 3.0.0
info:
  title: StoryDream Framework API
  version: 1.0.0
servers:
  - url: https://api.github.com
paths:
  /repos/jeruzz/StoryDream-FRAMEWORK/contents/{path}:
    get:
      summary: Obtener contenido de archivo
      parameters:
        - name: path
          in: path
          required: true
          schema:
            type: string
      security:
        - BearerAuth: []
components:
  securitySchemes:
    BearerAuth:
      type: http
      scheme: bearer
```

## Notas Importantes

1. **Token de Solo Lectura**: El token actual tiene permisos de solo lectura (Contents: Read-only)
2. **Expiración**: El token expira el 16 de febrero de 2026
3. **Repositorio Público**: Aunque el repo es público, el token permite control de acceso
4. **Rate Limits**: GitHub API tiene límite de 5000 requests/hora con autenticación

## Contacto
Repositorio mantenido por @jeruzz
