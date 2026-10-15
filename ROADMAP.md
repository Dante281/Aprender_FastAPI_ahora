# 🚀 Proyecto Guiado: FastAPI + LLM Local (Curso HolaMundo)

- **Vídeo de referencia:** `Tienes que aprender FastAPI ahora, es increíble!` (52:15)
- **Objetivo:** Construir una API REST modular desde cero y conectarla de forma asíncrona a un LLM local, documentando cada bloque mediante commits progresivos.

## 📅 Fases del Proyecto

### 🟢 Fase 1: Entorno, "Hola Mundo" y Swagger UI `[00:05:24 - 00:12:42]`
- [x] Inicializar proyecto moderno con `uv init --app .` (o `uv init`) configurando `pyproject.toml` y `.venv`.
- [x] Añadir dependencias con `uv add "fastapi[standard]"` (generando `uv.lock`).
- [ ] Crear `main.py` con la instancia `app = FastAPI()` y la ruta raíz `@app.get("/")` que devuelva `{"mensaje": "Hola mundo"}`.
- [ ] Levantar el servidor con `uv run fastapi dev main.py`.
- [ ] Probar la respuesta JSON y explorar Swagger UI en `http://127.0.0.1:8000/docs`.
- [ ] 📝 Documentar conceptos y flujo de trabajo con `uv` en `docs/notas.md`.
- [ ] Commit: `feat(init): setup project environment with uv and root endpoint`

### 🟡 Fase 2: Rutas, Path Params y Query Params `[00:12:54 - 00:20:08]`
- [ ] Crear `@app.get("/products")` que devuelva `{"products": []}`.
- [ ] Crear `@app.get("/products/{product_id}")` recibiendo `product_id: int`.
- [ ] Probar error `422 Unprocessable Entity` pasando un string en lugar de int.
- [ ] Añadir Query Parameter `limit: int = 10` en `get_products`.
- [ ] Combinar Path y Query Parameter (`include_desc: bool = False`) en `get_product`.
- [ ] 📝 Documentar diferencia entre Path y Query Params en `docs/notas.md`.
- [ ] Commit: `feat(products): add path and query parameters with type validation`

### 🟠 Fase 3: Esquemas de Datos y Validaciones con Pydantic `[00:20:08 - 00:28:32]`
- [ ] Crear `schemas.py` e importar `BaseModel` y `Field` de `pydantic`.
- [ ] Definir `Product(BaseModel)` con `name: str = Field(min_length=3)`, `description: str | None = None`, `price: float = Field(gt=0)`, `stock: int = Field(gt=0)`.
- [ ] Crear `@app.post("/products", status_code=201)` recibiendo `product: Product`.
- [ ] Probar validaciones en `/docs` con datos inválidos.
- [ ] 📝 Documentar validación de Request Body y `Field` en `docs/notas.md`.
- [ ] Commit: `feat(schemas): implement Pydantic Product model and Field validations`

### 🔵 Fase 4: CRUD en Memoria y Manejo de Errores HTTP `[00:28:32 - 00:36:19]`
- [ ] En `schemas.py`, añadir `id: int | None = None` a `Product` y cambiar `stock` a `Field(ge=0)`.
- [ ] En `main.py`, crear `products: dict[int, Product] = {}` y `next_id = 1`.
- [ ] Implementar guardado con ID autoincremental en `POST /products`.
- [ ] Devolver `list(products.values())[:limit]` en `GET /products`.
- [ ] Implementar búsqueda en `GET /products/{product_id}` y borrado en `DELETE /products/{product_id}`.
- [ ] Lanzar `HTTPException(status_code=404, detail="Producto no encontrado")` cuando el ID no exista en GET y DELETE.
- [ ] 📝 Documentar manejo de errores y códigos de estado HTTP en `docs/notas.md`.
- [ ] Commit: `feat(crud): complete in-memory CRUD and 404 HTTPException handling`

### 🟣 Fase 5: Arquitectura Profesional con `APIRouter` y `storage.py` `[00:36:19 - 00:41:47]`
- [ ] Extraer el diccionario `products` y `next_id` a un nuevo archivo `storage.py`.
- [ ] Crear `routers/products.py` con `router = APIRouter(prefix="/products", tags=["products"])`.
- [ ] Mover las rutas de productos al router y conectarlo con `storage.py`.
- [ ] Registrar el router en `main.py` con `app.include_router(products_router)`.
- [ ] 📝 Documentar modularización con `APIRouter` en `docs/notas.md`.
- [ ] Commit: `refactor(routers): modularize product routes and storage layer`

### 🔴 Fase 6: Integración Asíncrona con LLM Local `[00:41:47 - 00:50:19]`
- [ ] Levantar servidor de LLM local en `/v1/chat/completions`.
- [ ] Añadir cliente HTTP asíncrono con `uv add httpx`.
- [ ] Crear `routers/llm.py` con `APIRouter(prefix="/llm", tags=["llm"])` y modelo `Question(BaseModel)` con `prompt: str`.
- [ ] Crear `@router.post("/ask")` asíncrono (`async def ask(question: Question)`).
- [ ] Conectar mediante `httpx.AsyncClient(timeout=600)` con `await client.post(...)` al modelo local y devolver `{"answer": ...}`.
- [ ] Registrar `llm_router` en `main.py` y probar en Swagger UI.
- [ ] 📝 Documentar peticiones asíncronas con `httpx` e integración con LLMs locales en `docs/notas.md`.
- [ ] Commit: `feat(llm): integrate local LLM chat completion endpoint via httpx`

### 🌟 Fase 7 (Bonus): Conectar el LLM con el Catálogo de Productos
- [ ] Crear un endpoint que use el LLM local para generar automáticamente descripciones de productos o responder consultas sobre el stock actual en `storage.py`.
- [ ] Añadir herramientas de pruebas con `uv add --dev pytest` y ejecutar con `uv run pytest`.
