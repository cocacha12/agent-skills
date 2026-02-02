---
name: Coolify Python Deployment
description: Guía paso a paso para desplegar proyectos Python desde GitHub en Coolify usando Nixpacks o Dockerfile.
topics:
  - Python
  - Coolify
  - Deployment
  - Nixpacks
  - Docker
use_cases:
  - Desplegar servicios Python (FastAPI, Flask, Django)
  - Configuración de variables de entorno en Coolify
  - Troubleshooting de despliegues automáticos
---

# Despliegue de Proyectos Python en Coolify desde GitHub

Esta guía detalla cómo configurar y desplegar una aplicación Python en Coolify extrayendo el código directamente desde un repositorio de GitHub.

## 1. Requisitos Previos

- Tener **Coolify** instalado y accesible.
- Un repositorio en **GitHub** con tu proyecto Python.
- Un archivo de dependencias en la raíz: `requirements.txt`, `pyproject.toml` (Poetry) o `setup.py`.

---

## 2. Despliegue con Nixpacks (Recomendado)

Nixpacks es el constructor por defecto en Coolify. Detecta automáticamente Python e instala las dependencias.

### Pasos:
1. **Crear Recurso**: En Coolify, ve a tu Proyecto -> **Add New Resource** -> **Git Repository**.
2. **Conectar GitHub**: Selecciona tu cuenta de GitHub y el repositorio deseado.
3. **Build Pack**: Asegúrate de que **Nixpacks** esté seleccionado (es el predeterminado).
4. **Configurar Puerto**: En la sección de **Network**, define el puerto en el que escucha tu app (ej. `8000` para FastAPI/Uvicorn).
5. **Comandos Personalizados**: 
   - Si necesitas un comando de inicio específico, edita el campo **Start Command**. 
   - Ejemplo: `uvicorn main:app --host 0.0.0.0 --port $PORT`

---

## 3. Despliegue con Dockerfile (Control Total)

Si tienes una configuración compleja, usa un `Dockerfile` en la raíz de tu repo.

### Ejemplo de Dockerfile base:
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["python", "run.py"]
```

### Pasos:
1. Al crear el recurso, elige **Dockerfile** como **Build Pack**.
2. Coolify leerá automáticamente el archivo `Dockerfile` de tu repositorio.

---

## 4. Variables de Envorno

Puedes configurar variables de entorno (`.env`) directamente en la pestaña **Environment Variables** del recurso en Coolify.
- Copia y pega el contenido de tu `.env` local.
- Asegúrate de marcar aquellas que sean sensibles como "Secret".

---

## 5. Solución de Problemas (Troubleshooting)

- **Puerto Incorrecto**: El error más común es que el puerto configurado en Coolify no coincida con el puerto en el que la aplicación escucha dentro del contenedor.
- **Dependencias de Sistema**: Si tu proyecto necesita librerías de sistema (ej. `libpq-dev` para PostgreSQL), Nixpacks suele detectarlo, pero en un Dockerfile deberás instalarlas manualmente vía `apt-get`.
- **Poetry**: Si usas Poetry, Nixpacks lo soporta, pero a veces es más robusto generar un `requirements.txt` antes de subir el código.
