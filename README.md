# ⚡ Laboratorio Práctico: FastAPI + LLM Local

Repositorio de estudio incremental y práctica guiada para el desarrollo de APIs modernas en Python con **FastAPI**, validación de esquemas con **Pydantic**, arquitectura modular con **`APIRouter`** e integración asíncrona (`httpx`) con modelos de lenguaje locales (**LLMs**).

---

## 🙌 Créditos y Autoría Original

Todo el diseño curricular, los ejercicios base y la estructura conceptual de este proyecto están basados en el curso gratuito publicado por **Nicolás Schurmann** en su canal **HolaMundo**:

* 📺 **Vídeo original:** [Tienes que aprender FastAPI ahora, es increíble!](https://www.youtube.com/watch?v=WrnFtgGLO38)
* 👨‍🏫 **Autor:** Nicolás Schurmann ([@HolaMundoDev](https://www.youtube.com/@HolaMundoDev) / [Academia Hola Mundo](https://academia.holamundo.io/))

> Este repositorio tiene fines exclusivamente educativos y de documentación personal, dividiendo el contenido del vídeo en fases prácticas y commits progresivos.

---

## 🗂️ Estructura del Repositorio

* [`ROADMAP.md`](./ROADMAP.md): Hoja de ruta dividida en 6 fases incrementales (más fase bonus) con marcas de tiempo y checklists.
* [`docs/notas.md`](./docs/notas.md): Bitácora técnica y apuntes detallados de cada bloque completado.
* [`AGENTS.md`](./AGENTS.md): Reglas de contexto para asistencia y revisión de código con IA (Google Antigravity) sin spoilers.

---

## 🛠️ Stack Tecnológico

* **Lenguaje:** Python 3.12+
* **Framework Web:** FastAPI (`fastapi[standard]`)
* **Validación de Datos:** Pydantic v2 (`BaseModel`, `Field`)
* **Cliente HTTP Asíncrono:** `httpx` (`AsyncClient`)
* **Inferencia Local:** Servidor LLM local compatible con OpenAI API (`/v1/chat/completions`)