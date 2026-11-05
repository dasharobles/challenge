# Challenge: Simulador de entrevistas técnicas

Aplicación Streamlit que realiza una entrevista adaptativa con Gemini para una de tres vacantes. Acepta tres respuestas técnicas, rechaza intentos de distracción sin consumir un turno y genera al final un reporte Markdown con calificación, fortalezas, áreas de mejora y dictamen.

## Archivos

- `app.py`: interfaz, flujo de entrevista, estado de sesión y evaluación.
- `requirements.txt`: dependencias para instalación local y Streamlit Cloud.
- `.gitignore`: evita subir secretos y archivos temporales.

## 1. Requisitos

- Python 3.10 o posterior.
- Una clave de Gemini API de Google AI Studio.
- Una cuenta de GitHub para publicar el repositorio.
- Una cuenta de Streamlit Community Cloud para el despliegue.

## 2. Configuración local de la clave

Desde esta carpeta crea `.streamlit/secrets.toml` con este contenido y reemplaza el texto entre comillas por una clave nueva:

```toml
GEMINI_API_KEY = "PEGA_AQUI_TU_CLAVE_NUEVA"
```

No incluyas este archivo en GitHub. `.gitignore` ya lo excluye. Si habías usado las claves incluidas en archivos de prácticas anteriores, revócalas y usa una nueva.

## 3. Instalación y ejecución

Abre PowerShell o la terminal de VS Code en esta carpeta y ejecuta:

```powershell
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Se abrirá la aplicación en el navegador, normalmente en `http://localhost:8501`.

## 4. Flujo de la aplicación

1. Selecciona Python Junior, Frontend o Integrador de APIs/Bots.
2. Pulsa **Iniciar entrevista**. Gemini genera la pregunta 1.
3. Responde cada pregunta. Las preguntas siguientes reciben contexto de las respuestas anteriores y del rol.
4. Las solicitudes que intentan desviar la conversación reciben una redirección y no cuentan como respuesta técnica.
5. Después de la respuesta 3, se cierra la etapa de preguntas y se genera el dictamen. No se permite una pregunta 4.
6. **Reiniciar Entrevista** limpia el rol, contador, historial y reporte.

## 5. Comprobación manual de la rúbrica

- Selecciona Python Junior y confirma que las preguntas correspondan a Python.
- Reinicia, selecciona Frontend y confirma que las preguntas sean sobre desarrollo web.
- Intenta una distracción y comprueba que la pregunta pendiente se repita y el contador no aumente.
- Contesta tres preguntas y comprueba que aparezca el reporte, sin una cuarta pregunta.
- Reinicia y comprueba que el contador vuelva a cero y se limpie el historial.
- Revisa que el reporte incluya nota del 1 al 10, al menos dos fortalezas, dos áreas de mejora y un dictamen APROBADO o NO APROBADO.

## 6. Publicación en GitHub

1. Crea un repositorio nuevo (público si la materia requiere acceso público).
2. Sube `app.py`, `requirements.txt`, `.gitignore` y este README.
3. Antes de publicar, verifica que `.streamlit/secrets.toml` no esté en los archivos seleccionados.

## 7. Despliegue en Streamlit Community Cloud

1. Entra a `https://share.streamlit.io/` y conecta tu cuenta de GitHub.
2. Selecciona **Create app** y el repositorio, rama y ruta `app.py`.
3. En **Advanced settings → Secrets**, agrega:

   ```toml
   GEMINI_API_KEY = "TU_CLAVE_NUEVA"
   ```

4. Guarda y pulsa **Deploy**. Espera a que termine el despliegue y abre la URL `*.streamlit.app`.

## Entregables de la práctica

- URL pública de la aplicación desplegada.
- URL del repositorio que contiene `app.py` y `requirements.txt`.
- Captura de la conversación completa de tres preguntas y del reporte final.
