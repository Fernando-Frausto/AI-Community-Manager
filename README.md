# 🤖 AI Community Manager & Content Curator

Un pipeline de Inteligencia Artificial *End-to-End* diseñado para automatizar la moderación, curaduría y generación de contenido (Copywriting) a partir de comunidades de Discord. 

Este proyecto transforma una ráfaga de mensajes crudos en publicaciones listas para redes sociales corporativas, utilizando inyección dinámica de personalidad (RAG) y arquitecturas de datos estrictas.

## 🚀 Características Principales (Features)

*   **Triaje Analítico Estricto:** Utiliza el modelo Llama 3.3 para evaluar mensajes y asignar un KPI de relevancia (0-100), separando el ruido (saludos, quejas) del valor (casos de éxito, vacantes).
*   **Structured Output (Pydantic):** Abandona el *prompting* tradicional de texto libre. La IA está forzada nativamente a devolver un objeto de datos JSON perfecto, eliminando errores de parseo.
*   **Inyección Dinámica de Marca (RAG Básico):** El sistema adapta su tono, vocabulario y emojis en tiempo real leyendo un archivo `.txt` (Manual de Marca) cargado por el usuario, sin modificar el código fuente.
*   **Sistema "Human-in-the-Loop":** Interfaz gráfica interactiva que permite a un Community Manager rescatar mensajes descartados por el filtro algorítmico, forzando a una segunda IA creativa a reescribirlos.
*   **Exportación B2B (Hand-off):** Módulo de descarga JSON con los activos finales estructurados para integrarse con herramientas de automatización (Zapier, Make, etc.).

## 🛠️ Stack Tecnológico

*   **Backend & LLM:** Python, LangChain, Groq API (Llama-3.3-70b-versatile).
*   **Estructuración de Datos:** Pydantic (Function Calling / Structured Outputs).
*   **Frontend / UI:** Streamlit (Métricas en tiempo real, Tabs multicanal, File Uploader).
*   **Data Mocking:** JSON local para simulación de Ingesta (Arquitectura Desacoplada).

## ⚙️ Arquitectura del Sistema

1.  **Cerebro IA (`cerebro_ia.py`):** Contiene las plantillas de LangChain y la definición de esquemas de Pydantic. Aloja dos cadenas: la *Cadena de Filtro* (estricta) y la *Cadena de Rescate* (creativa).
2.  **Dashboard Visual (`app.py`):** Gestiona el estado de la sesión, renderiza los KPIs ejecutivos e interactúa con el usuario para la inyección del manual de marca.
3.  **Contrato de Datos:** El sistema espera un input estandarizado (`id`, `autor`, `canal`, `texto`) para asegurar que el backend pueda conectarse a cualquier fuente (Discord, Slack, Telegram).

## 🚀 Cómo ejecutarlo localmente

1. Clona el repositorio:
   ```bash
   git clone [https://github.com/tu-usuario/AI-Community-Manager.git](https://github.com/tu-usuario/AI-Community-Manager.git)
2. Instala las dependencias (se recomienda un entorno virtual):
   ```bash
   pip install langchain langchain-core langchain-groq pydantic streamlit python-dotenv
3. Crea un archivo .env en la raíz con tus credenciales:
   ```Fragmento de código
   GROQ_API_KEY=tu_clave_aqui
   DISCORD_TOKEN=tu_clave_aqui
4. Levanta el servidor local de Streamlit
   ```bash
   python -m streamlit run app.py
