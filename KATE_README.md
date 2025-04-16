# KATE – Kubernetes Application Telemetry & Exploration

**KATE** (por “K8” y en honor a Katherine Johnson) es una aplicación web para visualizar e interactuar con el estado de un clúster de Kubernetes desde fuera del propio clúster. Está dividida en microservicios independientes que se comunican mediante APIs REST.

---

## MVP Obligatorio

### Objetivo

- Conectar desde fuera del clúster a un clúster Kubernetes usando credenciales.
- Consultar el estado de los pods (nombre, estado, tiempo de inicio, namespace…).
- Visualizar la arquitectura del clúster en una interfaz 3D con Three.js.
- Interactuar con los pods (detener, eliminar, reiniciar…).

### Servicios del MVP

#### 1. `kate-controller-api` (Spring Boot + Fabric8)
- Conecta con el clúster Kubernetes desde fuera.
- Obtiene información de los pods.
- Permite ejecutar acciones sobre los pods.
- Expone un API REST para el frontend.

#### 2. `kate-frontend` (Three.js + Tailwind)
- Visualiza el estado de los pods de forma gráfica en 3D.
- Permite seleccionar e interactuar con los pods.
- Consume el API REST del microservicio backend.

---

## Extensiones Opcionales

### `kate-state-logger`
- Microservicio que guarda periódicamente el estado de los pods en MySQL.
- Permite consultas históricas del estado del clúster.

### `kate-user-auth`
- Autenticación de usuarios con FastAPI y JWT.
- Gestión de tokens para controlar el acceso a los endpoints del backend.

### `kate-user-tracker`
- Registra las acciones que hace cada usuario (reinicios, eliminaciones…).
- Almacena logs en base de datos (MySQL o MongoDB).

---

## Estructura del proyecto

```
kate/
├── kate-controller-api/       # API REST para control y consulta de pods
├── kate-frontend/             # Interfaz 3D con Three.js
├── kate-state-logger/         # [Opcional] Historial de estado
├── kate-user-auth/            # [Opcional] Autenticación de usuarios
├── kate-user-tracker/         # [Opcional] Registro de acciones
└── docker-compose.yml         # [Opcional] Levanta servicios auxiliares
```

---

## Acceso al clúster

El backend se conecta al clúster desde fuera. Para ello:

- Usa un fichero `kubeconfig` local.
- O bien un token de acceso asociado a una cuenta de servicio.

---

## Tecnologías principales

- **Backend:** Spring Boot, Fabric8, Java 21
- **Frontend:** Three.js, TailwindCSS
- **Bases de datos (opcionales):** MySQL, MongoDB
- **Autenticación:** FastAPI, JWT
- **Contenedores:** Docker, Docker Compose
- **Orquestación:** Kubernetes

---

## Estado del proyecto

Trabajo de Fin de Ciclo de Desarrollo de Aplicaciones Web. En desarrollo.