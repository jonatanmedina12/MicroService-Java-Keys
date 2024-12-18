# Repositorio de Configuración - Microservicios 🔐

Este repositorio contiene los archivos de configuración centralizados para todos los microservicios de la aplicación. El Config Server accede a estos archivos para distribuir la configuración a cada servicio.

## 📁 Estructura del Repositorio

```
├── application.yml               # Configuración común para todos los servicios
├── discovery-server.yml         # Configuración del Eureka Server
├── api-gateway.yml             # Configuración del API Gateway
├── companies-crud/
│   ├── companies-crud.yml     # Configuración base
│   ├── companies-crud-dev.yml # Configuración para desarrollo
│   └── companies-crud-qa.yml  # Configuración para QA
├── report-ms/
│   ├── report-ms.yml         # Configuración base
│   ├── report-ms-dev.yml    # Configuración para desarrollo
│   └── report-ms-qa.yml     # Configuración para QA
└── report-listener/
    ├── report-listener.yml  # Configuración base
    └── report-listener-qa.yml # Configuración para QA
```

## 🔑 Gestión de Claves Sensibles

- Las credenciales y datos sensibles están encriptados
- Se utiliza el algoritmo de encriptación simétrica
- Las claves encriptadas comienzan con `{cipher}`

### Ejemplo de Configuración Encriptada:
```yaml
spring:
  datasource:
    username: myuser
    password: '{cipher}AQA6EN7aXNXrBiIv...'
```

## 🔧 Perfiles de Configuración

- **default**: Configuración base
- **dev**: Entorno de desarrollo
- **qa**: Entorno de pruebas
- **prod**: Entorno de producción

## 📚 Convenciones de Nombrado

Los archivos siguen el patrón:
```
{application-name}-{profile}.yml
```

Ejemplo:
- `companies-crud-dev.yml`
- `report-ms-qa.yml`

## 🔒 Seguridad

1. **Encriptación**
   - Usar la herramienta de encriptación proporcionada por Spring Cloud Config
   - No commitear valores sensibles sin encriptar

2. **Acceso**
   - Control de acceso basado en roles
   - Autenticación requerida para acceder a la configuración



2. **Agregar nueva configuración**
   - Crear archivo YML con el nombre del servicio
   - Seguir la estructura de carpetas establecida
   - Encriptar valores sensibles

3. **Encriptar valores**
   ```bash
   curl http://config-server:8888/encrypt -d "valor-a-encriptar"
   ```

4. **Actualizar configuración**
   ```bash
   git add .
   git commit -m "Actualización de configuración"
   git push origin main
   ```

## 📋 Validación

Para validar cambios:
1. Verificar sintaxis YAML
2. Confirmar que las claves estén encriptadas
3. Probar la configuración en ambiente de desarrollo
4. Realizar commit solo después de validación exitosa

## ⚠️ Consideraciones

- No almacenar claves privadas
- Mantener backups de las configuraciones
- Documentar todos los cambios significativos
- Seguir el princ
