# Bitácora y Apuntes Técnicos - FastAPI + LLM Local

Notas, conceptos clave y comandos aprendidos durante el desarrollo guiado del proyecto.

---

## 🟢 Fase 1: Entorno, "Hola Mundo" y Swagger UI

### 1. Gestión de Entornos Modernos con Astral `uv`
En lugar del flujo clásico de `python -m venv` y `pip install -r requirements.txt`, se utiliza **`uv`**, un gestor de paquetes de alto rendimiento escrito en Rust:
* **`pyproject.toml` (PEP 621):** Archivo estándar y declarativo donde se definen los metadatos del proyecto y las dependencias directas (`dependencies = ["fastapi[standard]>=..."]`).
* **`uv.lock`:** Lockfile determinista que congela las versiones exactas de las 58 dependencias directas e indirectas instaladas, garantizando builds 100% reproducibles.
* **`.venv/`:** Entorno virtual aislado creado automáticamente en el directorio del proyecto.

#### Comandos fundamentales ejecutados:
```powershell
# Inicializar el proyecto con estructura de aplicación
uv init --app .

# Añadir FastAPI con el bundle estándar de utilidades
uv add "fastapi[standard]"
```

### 2. ¿Qué incluye `fastapi[standard]`?
El extra `standard` instala automáticamente los componentes esenciales para desarrollo:
* **`fastapi`:** Framework web para construir APIs de alto rendimiento con tipado estricto.
* **`uvicorn[standard]`:** Servidor ASGI para servir las peticiones HTTP y WebSockets.
* **`fastapi-cli`:** CLI oficial que aporta comandos como `fastapi dev` (servidor con recarga automática para desarrollo).
* **`pydantic` v2:** Motor ultra-rápido de validación de datos basado en tipos estándar de Python.
* **Utilidades complementarias:** `httpx`, `python-multipart`, `email-validator`, etc.

### 3. Próximos pasos pendientes (Fase 1)
* [ ] Crear `main.py` con la instancia `app = FastAPI()`.
* [ ] Definir el endpoint raíz `@app.get("/")`.
* [ ] Ejecutar el servidor con `uv run fastapi dev main.py`.
* [ ] Explorar la documentación interactiva OpenAPI en `http://127.0.0.1:8000/docs` (Swagger UI).

---

## 🟡 Fase 2: Rutas, Path Params y Query Params

*Pendiente de documentar.*

---

## 🟠 Fase 3: Esquemas de Datos y Validaciones con Pydantic

*Pendiente de documentar.*

---

## 🔵 Fase 4: CRUD en Memoria y Manejo de Errores HTTP

*Pendiente de documentar.*

---

## 🟣 Fase 5: Arquitectura Profesional con `APIRouter` y `storage.py`

*Pendiente de documentar.*

---

## 🔴 Fase 6: Integración Asíncrona con LLM Local

*Pendiente de documentar.*

---

## 🌟 Fase 7 (Bonus): Conectar el LLM con el Catálogo de Productos

*Pendiente de documentar.*
