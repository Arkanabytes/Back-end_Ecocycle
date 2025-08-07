# EcoCycle Backend 🌱♻️

**EcoCycle** es una plataforma integral de reciclaje de residuos diseñada para armonizar, recompensar y empoderar a los actores del ecosistema de reciclaje, con un enfoque en los esfuerzos de mitigación del cambio climático en mercados emergentes.

## 🎯 Descripción del Proyecto

EcoCycle conecta recolectores y procesadores de residuos a través de una innovadora plataforma impulsada por blockchain que incentiva prácticas sostenibles de gestión de residuos. La plataforma facilita transacciones transparentes, precios justos y seguimiento del impacto ambiental mediante contratos inteligentes y recompensas tokenizadas.

### Características Principales

- **Ecosistema Multi-actor**: Conecta recolectores, procesadores y organizaciones ambientales
- **Integración Blockchain**: Transacciones seguras y transparentes usando stablecoins
- **Sistema de Recompensas por Tokens**: EcoTokens incentivan la participación y prácticas sostenibles  
- **Seguimiento de Impacto**: Métricas e informes de impacto ambiental en tiempo real
- **Diseño Mobile-First**: Interfaz accesible para trabajadores de campo y pequeños negocios

## 🏗️ Arquitectura del Sistema

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  App Móvil      │    │  Portal Web     │    │  Panel Admin    │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌─────────────────┐
                    │  API Gateway    │
                    └─────────┬───────┘
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
┌─────────┴───────┐  ┌─────────┴───────┐  ┌─────────┴───────┐
│ Servicio Usuario│  │Servicio de Pago │  │Servicio Impacto │
└─────────────────┘  └─────────────────┘  └─────────────────┘
          │                   │                   │
          └───────────────────┼───────────────────┘
                              │
                    ┌─────────────────┐
                    │  Base de Datos  │
                    └─────────────────┘
```

## 🚀 Comenzando

### Prerequisitos

- **Node.js** (v18+ recomendado)
- **MongoDB** (v6.0+)
- **Redis** (para caché)
- **Docker** (opcional, para containerización)
- **npm** o **yarn** como gestor de paquetes

### Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/Arkanabytes/Back-end_Ecocycle.git
   cd Back-end_Ecocycle
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   # o
   yarn install
   ```

3. **Configuración del entorno**
   ```bash
   cp .env.example .env
   ```
   Configurar las siguientes variables de entorno:
   ```env
   NODE_ENV=development
   PORT=3000
   
   # Base de datos
   MONGODB_URI=mongodb://localhost:27017/ecocycle
   REDIS_URL=redis://localhost:6379
   
   # JWT
   JWT_SECRET=tu_secreto_jwt_aqui
   JWT_EXPIRES_IN=7d
   
   # Blockchain
   BLOCKCHAIN_NETWORK=testnet
   CONTRACT_ADDRESS=0x...
   PRIVATE_KEY=tu_clave_privada
   
   # APIs externas
   PAYMENT_GATEWAY_API_KEY=tu_clave_de_pago
   SMS_SERVICE_API_KEY=tu_clave_sms
   ```

4. **Configuración de la base de datos**
   ```bash
   npm run db:migrate
   npm run db:seed
   ```

5. **Iniciar la aplicación**
   ```bash
   # Desarrollo
   npm run dev
   
   # Producción
   npm run build
   npm start
   ```

## 📖 Documentación de la API

### Endpoints de Autenticación

```http
POST /api/v1/auth/registro
POST /api/v1/auth/login
POST /api/v1/auth/refresh
POST /api/v1/auth/recuperar-password
```

### Gestión de Usuarios

```http
GET    /api/v1/usuarios/perfil
PUT    /api/v1/usuarios/perfil
POST   /api/v1/usuarios/verificar-telefono
GET    /api/v1/usuarios/transacciones
```

### Gestión de Residuos

```http
GET    /api/v1/residuos/categorias
POST   /api/v1/residuos/publicaciones
GET    /api/v1/residuos/publicaciones
PUT    /api/v1/residuos/publicaciones/:id
DELETE /api/v1/residuos/publicaciones/:id
```

### Transacciones

```http
POST   /api/v1/transacciones/crear
GET    /api/v1/transacciones
GET    /api/v1/transacciones/:id
POST   /api/v1/transacciones/:id/completar
```

### Gestión de Tokens

```http
GET    /api/v1/tokens/saldo
POST   /api/v1/tokens/transferir
GET    /api/v1/tokens/historial
POST   /api/v1/tokens/canjear
```

Para documentación detallada de la API, visita: `http://localhost:3000/api-docs` (Swagger UI)

## 🗄️ Esquema de Base de Datos

### Entidades Principales

- **Usuarios**: Recolectores, procesadores y administradores
- **PublicacionesResiduos**: Materiales de residuos disponibles para recolección
- **Transacciones**: Registros de pagos y transferencias de residuos
- **Tokens**: Saldo e historial de transacciones de EcoTokens
- **Categorias**: Clasificaciones de tipos de residuos
- **Ubicaciones**: Datos geográficos de puntos de recolección/entrega

## 🔒 Características de Seguridad

- **Autenticación JWT**: Autenticación segura basada en tokens
- **Limitación de Velocidad**: Control de solicitudes a la API
- **Validación de Entrada**: Sanitización integral de datos
- **Protección CORS**: Filtrado de solicitudes cross-origin  
- **Encriptación**: Cifrado de datos sensibles en reposo
- **Seguridad Blockchain**: Medidas de seguridad en contratos inteligentes

## 🧪 Pruebas

```bash
# Pruebas unitarias
npm run test

# Pruebas de integración  
npm run test:integration

# Pruebas end-to-end
npm run test:e2e

# Cobertura de pruebas
npm run test:coverage
```

## 🏗️ Despliegue

### Despliegue con Docker

```bash
# Construir imagen
docker build -t ecocycle-backend .

# Ejecutar contenedor
docker run -p 3000:3000 --env-file .env ecocycle-backend
```

### Despliegue en Producción

```bash
# Construir para producción
npm run build

# Iniciar con PM2
npm run start:prod
```

## 🤝 Contribuyendo

¡Damos la bienvenida a contribuciones de la comunidad! Por favor sigue estos pasos:

1. **Hacer Fork** del repositorio
2. **Crear** una rama de característica (`git checkout -b feature/CaracteristicaIncreible`)
3. **Hacer Commit** de tus cambios (`git commit -m 'Agregar alguna CaracteristicaIncreible'`)
4. **Push** a la rama (`git push origin feature/CaracteristicaIncreible`)
5. **Abrir** un Pull Request

### Estándares de Código

- Seguir la configuración de **ESLint**
- Mantener **cobertura de pruebas del 80%+**
- Usar **commits convencionales**
- Actualizar documentación para nuevas características

## 📊 Monitoreo y Análisis

- **Métricas de Aplicación**: Tiempos de respuesta, tasas de error, rendimiento
- **Impacto Ambiental**: Reducción de CO2, residuos desviados de vertederos
- **Participación de Usuarios**: Usuarios activos, volúmenes de transacciones
- **Economía de Tokens**: Circulación de tokens, distribución de recompensas

## 🔧 Configuración

### Variables de Entorno

| Variable | Descripción | Por Defecto |
|----------|-------------|-------------|
| `NODE_ENV` | Entorno de la aplicación | `development` |
| `PORT` | Puerto del servidor | `3000` |
| `MONGODB_URI` | Cadena de conexión de base de datos | - |
| `REDIS_URL` | URL del servidor de caché | - |
| `JWT_SECRET` | Secreto para firmar JWT | - |
| `BLOCKCHAIN_NETWORK` | Red blockchain (mainnet/testnet) | `testnet` |

## 📈 Hoja de Ruta

### Fase 1: Plataforma Base (Actual)
- [x] Registro y autenticación de usuarios
- [x] Funcionalidad básica de publicación de residuos
- [x] Integración de procesamiento de pagos
- [ ] Finalización de API para app móvil

### Fase 2: Características Mejoradas (Q3 2025)
- [ ] Algoritmos de emparejamiento avanzados
- [ ] Integración de seguimiento en tiempo real
- [ ] Soporte multi-idioma
- [ ] Dashboard de análisis avanzado

### Fase 3: Escalabilidad y Crecimiento (Q4 2025)
- [ ] Despliegue multi-región
- [ ] Integraciones de socios
- [ ] Optimización potenciada por IA
- [ ] Mercado de créditos de carbono

## 🆘 Solución de Problemas

### Problemas Comunes

**Falló la Conexión a la Base de Datos**
```bash
# Verificar servicio MongoDB
sudo systemctl status mongod

# Verificar cadena de conexión
echo $MONGODB_URI
```

**Errores de Autenticación de Token**
```bash
# Verificar que el secreto JWT esté configurado
echo $JWT_SECRET

# Verificar expiración del token
curl -H "Authorization: Bearer <token>" /api/v1/auth/verificar
```

## 📞 Soporte

- **Documentación**: [docs.ecocycle.io](https://docs.ecocycle.io)
- **Email**: soporte@ecocycle.io  
- **Discord**: [Comunidad EcoCycle](https://discord.gg/ecocycle)
- **Issues**: [GitHub Issues](https://github.com/Arkanabytes/Back-end_Ecocycle/issues)

## 📄 Licencia

Este proyecto está licenciado bajo la **Licencia MIT** - consulta el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Reconocimientos

- Comunidad de **Blockchain para Impacto Social**
- Marco de **Objetivos de Desarrollo Sostenible**
- Contribuyentes y mantenedores de **Código Abierto**
- **Organizaciones ambientales** que proporcionan orientación y retroalimentación

---

**Construido con ❤️ para un futuro sostenible** 🌍

[![GitHub stars](https://img.shields.io/github/stars/Arkanabytes/Back-end_Ecocycle?style=social)](https://github.com/Arkanabytes/Back-end_Ecocycle/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Arkanabytes/Back-end_Ecocycle?style=social)](https://github.com/Arkanabytes/Back-end_Ecocycle/network)
[![GitHub issues](https://img.shields.io/github/issues/Arkanabytes/Back-end_Ecocycle)](https://github.com/Arkanabytes/Back-end_Ecocycle/issues)
[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
