# 🌍 EcoCycle - Plataforma de Reciclaje Blockchain

![EcoCycle Logo](https://img.shields.io/badge/EcoCycle-Backend-green?style=for-the-badge&logo=recycling)
![Node.js](https://img.shields.io/badge/Node.js-v18+-green?style=flat&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-v6.0+-green?style=flat&logo=mongodb)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat)

> **EcoCycle** es una plataforma integral de reciclaje de residuos diseñada para armonizar, recompensar y empoderar a los actores del ecosistema de reciclaje, con un enfoque en los esfuerzos de mitigación del cambio climático en mercados emergentes.

## 🚀 Descripción del Proyecto

EcoCycle conecta recolectores y procesadores de residuos a través de una innovadora plataforma impulsada por blockchain que incentiva prácticas sostenibles de gestión de residuos. La plataforma facilita transacciones transparentes, precios justos y seguimiento del impacto ambiental mediante contratos inteligentes y recompensas tokenizadas.

### ✨ Características Principales

- 🔗 **Ecosistema Multi-actor**: Conecta recolectores, procesadores y organizaciones ambientales
- ⛓️ **Integración Blockchain**: Transacciones seguras y transparentes usando stablecoins
- 🎁 **Sistema de Recompensas por Tokens**: EcoTokens incentivan la participación y prácticas sostenibles
- 📊 **Seguimiento de Impacto**: Métricas e informes de impacto ambiental en tiempo real
- 📱 **Diseño Mobile-First**: Interfaz accesible para trabajadores de campo y pequeños negocios

## 🏗️ Arquitectura del Sistema

```
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ App Móvil       │ │ Portal Web      │ │ Panel Admin     │
└─────────┬───────┘ └─────────┬───────┘ └─────────┬───────┘
          │                   │                   │
          └──────────────────────┼──────────────────────┘
                               │
                    ┌─────────────────┐
                    │ API Gateway     │
                    └─────────┬───────┘
                              │
    ┌───────────────────┼───────────────────┐
    │                   │                   │
┌─────────┴───────┐ ┌─────────┴───────┐ ┌─────────┴───────┐
│ Servicio Usuario│ │Servicio de Pago │ │Servicio Impacto │
└─────────────────┘ └─────────────────┘ └─────────────────┘
    │                   │                   │
    └───────────────────┼───────────────────┘
                        │
              ┌─────────────────┐
              │ Base de Datos   │
              └─────────────────┘
```

## 📋 Requisitos Previos

- **Node.js** (v18+ recomendado)
- **MongoDB** (v6.0+)
- **Redis** (para caché)
- **Docker** (opcional, para containerización)
- **npm** o **yarn** como gestor de paquetes

## 🛠️ Instalación

### 1. Clonar el repositorio
```bash
git clone https://github.com/Arkanabytes/Project_Ecocycle.git
cd Project_Ecocycle
```

### 2. Instalar dependencias
```bash
npm install
# o
yarn install
```

### 3. Configuración del entorno
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

### 4. Configuración de la base de datos
```bash
npm run db:migrate
npm run db:seed
```

### 5. Iniciar la aplicación
```bash
# Desarrollo
npm run dev

# Producción
npm run build
npm start
```

## 📚 API Endpoints

### 🔐 Autenticación
- `POST /api/v1/auth/registro` - Registro de usuario
- `POST /api/v1/auth/login` - Inicio de sesión
- `POST /api/v1/auth/refresh` - Renovar token
- `POST /api/v1/auth/recuperar-password` - Recuperar contraseña

### 👤 Usuarios
- `GET /api/v1/usuarios/perfil` - Obtener perfil
- `PUT /api/v1/usuarios/perfil` - Actualizar perfil
- `POST /api/v1/usuarios/verificar-telefono` - Verificar teléfono
- `GET /api/v1/usuarios/transacciones` - Historial de transacciones

### ♻️ Residuos
- `GET /api/v1/residuos/categorias` - Obtener categorías
- `POST /api/v1/residuos/publicaciones` - Crear publicación
- `GET /api/v1/residuos/publicaciones` - Listar publicaciones
- `PUT /api/v1/residuos/publicaciones/:id` - Actualizar publicación
- `DELETE /api/v1/residuos/publicaciones/:id` - Eliminar publicación

### 💰 Transacciones
- `POST /api/v1/transacciones/crear` - Crear transacción
- `GET /api/v1/transacciones` - Listar transacciones
- `GET /api/v1/transacciones/:id` - Obtener transacción
- `POST /api/v1/transacciones/:id/completar` - Completar transacción

### 🪙 Tokens
- `GET /api/v1/tokens/saldo` - Obtener saldo
- `POST /api/v1/tokens/transferir` - Transferir tokens
- `GET /api/v1/tokens/historial` - Historial de tokens
- `POST /api/v1/tokens/canjear` - Canjear tokens

> 📖 **Documentación detallada**: http://localhost:3000/api-docs (Swagger UI)

## 🗄️ Modelos de Datos

- **Usuarios**: Recolectores, procesadores y administradores
- **PublicacionesResiduos**: Materiales de residuos disponibles para recolección
- **Transacciones**: Registros de pagos y transferencias de residuos
- **Tokens**: Saldo e historial de transacciones de EcoTokens
- **Categorias**: Clasificaciones de tipos de residuos
- **Ubicaciones**: Datos geográficos de puntos de recolección/entrega

## 🔒 Seguridad

- **Autenticación JWT**: Autenticación segura basada en tokens
- **Limitación de Velocidad**: Control de solicitudes a la API
- **Validación de Entrada**: Sanitización integral de datos
- **Protección CORS**: Filtrado de solicitudes cross-origin
- **Encriptación**: Cifrado de datos sensibles en reposo
- **Seguridad Blockchain**: Medidas de seguridad en contratos inteligentes

## 🧪 Testing

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

## 🐳 Docker

```bash
# Construir imagen
docker build -t ecocycle-backend .

# Ejecutar contenedor
docker run -p 3000:3000 --env-file .env ecocycle-backend
```

## 🚀 Despliegue en Producción

```bash
# Construir para producción
npm run build

# Iniciar con PM2
npm run start:prod
```

## 📊 Monitoreo y Métricas

- **Métricas de Aplicación**: Tiempos de respuesta, tasas de error, rendimiento
- **Impacto Ambiental**: Reducción de CO2, residuos desviados de vertederos
- **Participación de Usuarios**: Usuarios activos, volúmenes de transacciones
- **Economía de Tokens**: Circulación de tokens, distribución de recompensas

## ⚙️ Variables de Entorno

| Variable | Descripción | Por Defecto |
|----------|-------------|-------------|
| `NODE_ENV` | Entorno de la aplicación | `development` |
| `PORT` | Puerto del servidor | `3000` |
| `MONGODB_URI` | Cadena de conexión de base de datos | - |
| `REDIS_URL` | URL del servidor de caché | - |
| `JWT_SECRET` | Secreto para firmar JWT | - |
| `BLOCKCHAIN_NETWORK` | Red blockchain (mainnet/testnet) | `testnet` |

## 🗺️ Roadmap

### ✅ Fase 1 (Completada)
- Registro y autenticación de usuarios
- Funcionalidad básica de publicación de residuos
- Integración de procesamiento de pagos

### 🚧 Fase 2 (En desarrollo)
- Finalización de API para app móvil
- Algoritmos de emparejamiento avanzados
- Integración de seguimiento en tiempo real

### 🔮 Fase 3 (Planificada)
- Soporte multi-idioma
- Dashboard de análisis avanzado
- Despliegue multi-región

### 🌟 Futuro
- Integraciones de socios
- Optimización potenciada por IA
- Mercado de créditos de carbono

## 🤝 Contribuir

¡Damos la bienvenida a contribuciones de la comunidad! Por favor sigue estos pasos:

1. Hacer Fork del repositorio
2. Crear una rama de característica (`git checkout -b feature/CaracteristicaIncreible`)
3. Hacer Commit de tus cambios (`git commit -m 'Agregar alguna CaracteristicaIncreible'`)
4. Push a la rama (`git push origin feature/CaracteristicaIncreible`)
5. Abrir un Pull Request

### 📝 Guías de Contribución
- Seguir la configuración de ESLint
- Mantener cobertura de pruebas del 80%+
- Usar commits convencionales
- Actualizar documentación para nuevas características

## 🔧 Troubleshooting

### Falló la Conexión a la Base de Datos
```bash
# Verificar servicio MongoDB
sudo systemctl status mongod

# Verificar cadena de conexión
echo $MONGODB_URI
```

### Errores de Autenticación de Token
```bash
# Verificar que el secreto JWT esté configurado
echo $JWT_SECRET

# Verificar expiración del token
curl -H "Authorization: Bearer <token>" /api/v1/auth/verificar
```

## 📞 Soporte

- **Documentación**: [docs.ecocycle.io](https://docs.ecocycle.io)
- **Email**: [soporte@ecocycle.io](mailto:soporte@ecocycle.io)
- **Discord**: [Comunidad EcoCycle](https://discord.gg/ecocycle)
- **Issues**: [GitHub Issues](https://github.com/Arkanabytes/Project_Ecocycle/issues)

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT - consulta el archivo [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- Comunidad de Blockchain para Impacto Social
- Marco de Objetivos de Desarrollo Sostenible
- Contribuyentes y mantenedores de Código Abierto
- Organizaciones ambientales que proporcionan orientación y retroalimentación

---

**Construido con ❤️ para un futuro sostenible** 🌍

[![GitHub stars](https://img.shields.io/github/stars/Arkanabytes/Back-end_Ecocycle?style=social)](https://github.com/Arkanabytes/Back-end_Ecocycle/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Arkanabytes/Back-end_Ecocycle?style=social)](https://github.com/Arkanabytes/Back-end_Ecocycle/network)
[![GitHub issues](https://img.shields.io/github/issues/Arkanabytes/Back-end_Ecocycle)](https://github.com/Arkanabytes/Back-end_Ecocycle/issues)
[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
