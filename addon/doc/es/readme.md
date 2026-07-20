# Documentación de Vision Assistant Pro

**Vision Assistant Pro** es un asistente de IA avanzado y multimodal para NVDA. Utiliza motores de IA de primer nivel para proporcionar lectura de pantalla inteligente, traducción, dictado por voz y análisis de documentos.

_Este complemento fue lanzado a la comunidad en honor al Día Internacional de las Personas con Discapacidad._

## 1. Configuración

Ve a **Menú de NVDA > Preferencias > Configuración > Vision Assistant Pro**.

### 1.1 Configuración de conexión
- **Proveedor:** Selecciona tu servicio de IA preferido. Los proveedores compatibles incluyen **Google Gemini**, **OpenAI**, **Mistral**, **Groq**, **MiniMax** y **Personalizado** (servidores compatibles con OpenAI como Ollama, LM Studio, Jan.ai o KoboldCPP).
- **Nota importante:** Recomendamos encarecidamente usar **Google Gemini** para obtener el mejor rendimiento y precisión (especialmente para análisis de imágenes/archivos).
- **Clave API:** Obligatorio. Puedes ingresar varias claves (separadas por comas o saltos de línea) para rotación automática.
- **Obtener modelos:** Después de ingresar tu clave API, presiona este botón para descargar la lista más reciente de modelos disponibles del proveedor.
- **Modelo de IA:** Selecciona el modelo principal utilizado para el chat general y análisis.

### 1.2 Enrutamiento avanzado de modelos
*Disponible para todos los proveedores, incluidos Gemini, OpenAI, Groq, Mistral y Personalizado.*

> **⚠️ Advertencia:** Estos ajustes están destinados **solo a usuarios avanzados**. Si no sabes qué hace un modelo específico, déjalo **desmarcado**. Seleccionar un modelo incompatible para una tarea (por ejemplo, un modelo solo de texto para Visión) causará errores y detendrá el funcionamiento del complemento.

Marca **"Enrutamiento avanzado de modelos (específico por tarea)"** para desbloquear el control detallado. Esto te permite seleccionar modelos específicos de la lista desplegable para diferentes tareas:
- **Modelo de OCR/Visión:** Elige un modelo especializado para analizar imágenes.
- **Texto a voz (STT):** Elige un modelo específico para dictado.
- **Voz a texto (TTS):** Elige un modelo para generar audio.
- **Modelo del Operador de IA:** Selecciona un modelo específico para tareas de operación autónoma del equipo.
- **Modelo de vídeo:** Selecciona un modelo específico para análisis de vídeo y generación de audiodescripción.
*Nota: Las funciones no compatibles (por ejemplo, TTS para Groq) se ocultarán automáticamente.*

### 1.3 Configuración avanzada de punto de acceso (Proveedor personalizado)
*Disponible solo cuando se selecciona "Personalizado".*

> **⚠️ Advertencia:** Esta sección permite la configuración manual de la API y está diseñada para **usuarios avanzados** que ejecutan servidores locales o proxies. URLs o nombres de modelos incorrectos interrumpirán la conectividad. Si no sabes exactamente qué son estos puntos de acceso, mantén esto **desmarcado**.

Marca **"Configuración avanzada de punto de acceso"** para ingresar manualmente los detalles del servidor. A diferencia de los proveedores nativos, aquí debes **escribir** las URLs específicas y los nombres de los modelos:
- **URL de lista de modelos:** El punto de acceso para obtener los modelos disponibles.
- **URL de punto de acceso OCR/STT/TTS:** URLs completas para servicios específicos (por ejemplo, `http://localhost:11434/v1/audio/speech`).
- **Modelos personalizados:** Escribe manualmente el nombre del modelo (por ejemplo, `llama3:8b`) para cada tarea.

### 1.3.1 Configurar IA local (Configuración en un paso)
Para hacer la integración con IA local completamente sin conexión extremadamente sencilla, hay un botón dedicado **"Configurar IA local"** disponible dentro de la Configuración del proveedor personalizado.

Si tienes un servidor de modelos de IA local en ejecución en tu equipo:
1. Selecciona **Personalizado** como tu proveedor.
2. Presiona el botón **Configurar IA local**.
3. Elige tu motor de IA local desde el diálogo accesible:
   - **Ollama** (por defecto en `http://127.0.0.1:11434`)
   - **LM Studio** (por defecto en `http://127.0.0.1:1234`)
   - **Jan.ai** (por defecto en `http://127.0.0.1:1337`)
   - **KoboldCPP** (por defecto en `http://127.0.0.1:5001`)
4. El complemento configurará instantáneamente la URL local correcta, el tipo de API, y obtendrá automáticamente tus modelos sin conexión activos para llenar el cuadro de selección del **Modelo de IA**.

*Nota sobre red y proxies:* Este motor de conexión local cuenta con un mecanismo avanzado de omisión de proxy. Incluso si tienes una VPN activa o un proxy en modo TUN, tus solicitudes de IA local lo omitirán completamente, garantizando conexiones sin conexión estables sin errores 502 Bad Gateway.

### 1.4 Preferencias generales
- **Motor OCR:** Elige entre **Chrome (Rápido)** para resultados rápidos o **IA (Avanzado)** para una mejor conservación del diseño.
- **Voz TTS:** Selecciona el estilo de voz que prefieras. Esta lista se actualiza dinámicamente según tu proveedor activo.
- **Creatividad (Temperatura):** Controla la aleatoriedad de la IA. Los valores más bajos son mejores para traducciones/OCR precisas.
- **URL del proxy:** Configura esto si los servicios de IA están restringidos en tu región (admite proxies locales como `127.0.0.1` o URLs puente).
- **Salida directa (sin ventana de chat):** Marca esto si quieres que la IA simplemente lea el resultado en voz alta sin abrir una ventana de chat interactiva.
- **Copiar respuestas de IA al portapapeles:** Copia automáticamente cada respuesta de la IA al portapapeles del sistema para facilitar el pegado.
- **Limpiar Markdown en el chat:** Desmarca esto si prefieres ver los símbolos de formato sin procesar en lugar de una vista de texto limpia y formateada.

## 2. Capa de comandos y atajos

Para evitar conflictos de teclado, este complemento usa una **Capa de comandos**.
1. Presiona **NVDA + Shift + V** (tecla maestra) para activar la capa (escucharás un pitido).
2. Suelta las teclas, luego presiona una de las siguientes teclas individuales:

| Tecla           | Función                          | Descripción                                                                 |
|-----------------|----------------------------------|-----------------------------------------------------------------------------|
| **Shift + A**   | **Operador de IA**               | **Operación autónoma:** Indica a la IA que realice una tarea en tu pantalla. Presionarlo de nuevo cancela las operaciones activas. |
| **E**           | **Explorador de interfaz**       | **Clic interactivo:** Identifica y hace clic en elementos de la interfaz en cualquier aplicación. |
| **T**           | Traductor inteligente            | Traduce el texto bajo el cursor del navegador o la selección.               |
| **Shift + T**   | Traductor del portapapeles       | Traduce el contenido que hay actualmente en el portapapeles.                |
| **R**           | Refinador de texto               | Resume, corrige gramática, explica o ejecuta **Indicaciones personalizadas**. |
| **V**           | Visión de objeto                 | Describe el objeto del navegador actual.                                    |
| **O**           | Visión de pantalla completa      | Analiza el diseño y contenido completo de la pantalla.                      |
| **Shift + V**   | Análisis de vídeo                | Analiza archivos de vídeo locales o vídeos en línea de **YouTube**, **Instagram**, **TikTok** o **Twitter (X)**. |
| **Control + V** | Grabación de vídeo local         | Graba un vídeo silencioso de tu pantalla y analiza las acciones y el diseño. |
| **D**           | Lector de documentos             | Lector avanzado de PDF e imágenes con selección de rango de páginas.        |
| **F**           | **Acción inteligente de archivo**| Reconocimiento contextual desde imagen, PDF o archivos TIFF seleccionados. |
| **A**           | Transcripción de audio           | Transcribe archivos MP3, WAV u OGG a texto.                                 |
| **C**           | Solucionador de CAPTCHA          | Captura y resuelve CAPTCHAs (compatible con portales gubernamentales).      |
| **S**           | Dictado inteligente              | Convierte voz a texto. Presiona para iniciar la grabación, vuelve a presionar para detener/escribir. |
| **Control+L**   | **Asistente en vivo**            | **Copiloto en tiempo real (solo Gemini):** Inicia o finaliza una conversación de voz y pantalla en vivo con el asistente de IA. |
| **I**           | Informe de estado                | Anuncia el progreso actual (por ejemplo, "Escaneando...", "Inactivo").      |
| **L**           | **Etiquetar objeto**             | **Etiquetado semántico con IA:** Etiqueta permanentemente el elemento/icono enfocado actualmente. |
| **Shift + L**   | **Administrar/Escanear etiquetas**| Abre el administrador de etiquetas (si existen etiquetas) o escanea la aplicación en busca de elementos sin nombre. |
| **U**           | Buscar actualizaciones           | Busca manualmente en GitHub la última versión del complemento.              |
| **Espacio**     | Recuperar último resultado       | Muestra la última respuesta de IA en un diálogo de chat para revisión o seguimiento. |
| **H**           | Ayuda de comandos                | Muestra una lista de todos los atajos disponibles.                          |
| **Alt + S**     | Configuración                    | Abre directamente el diálogo de configuración de Vision Assistant Pro.      |
| **Alt + Q**     | Informe de claves con cuota agotada | Informa sobre el número de claves API de Gemini que han superado su cuota diaria y cuándo se restablecerán. |
| **Alt + M**     | Auditoría de enrutamiento        | Informa sobre los modelos de IA actualmente seleccionados en el enrutamiento avanzado. |

## 3. Operador de IA — Control autónomo del equipo

El **Operador de IA** convierte Vision Assistant Pro de un lector pasivo en un asistente activo capaz de interactuar con tu equipo en tu nombre. Puedes pedirle que describa la pantalla, responda preguntas sobre lo que ve, o tome el control: hacer clic en botones, arrastrar elementos, escribir texto y navegar por aplicaciones mediante comandos en lenguaje natural.

La mayor ventaja es que funciona perfectamente en software completamente inaccesible. Si estás atascado en una aplicación personalizada, un escritorio remoto o un sitio web donde tu lector de pantalla permanece en silencio, al Operador no le importa. Como "ve" la pantalla visualmente, puede encontrar, leer e interactuar con elementos que no tienen ninguna etiqueta de accesibilidad.

### Cómo funciona
1. Presiona **NVDA + Shift + V**, luego presiona **Shift + A** para abrir el diálogo del Operador de IA.
2. Escribe lo que quieres hacer en lenguaje natural (por ejemplo, "Haz clic en el botón Guardar", "¿Qué dice el mensaje de error?" o "Cambia el nombre del archivo a final.pdf").
3. La IA analizará tu pantalla, identificará los elementos relevantes y realizará la acción o proporcionará la respuesta. Si una tarea requiere varios pasos, el Operador continuará trabajando hasta completarla.
4. Presiona **Shift + A** de nuevo en cualquier momento para cancelar una operación en curso al instante.

### Acciones compatibles
El Operador entiende una amplia gama de comandos:
- **Describir y responder**: "Describe el diseño de la pantalla" o "¿Qué dice el mensaje de error?"
- **Clic**: "Haz clic en el botón Guardar"
- **Clic derecho**: "Haz clic derecho en el archivo"
- **Doble clic**: "Haz doble clic en el documento"
- **Arrastrar y soltar**: "Arrastra el documento a la carpeta Archivo"
- **Escribir**: "Escribe 'Hola Mundo' en el cuadro de búsqueda"
- **Desplazar**: "Desplázate hacia abajo tres veces"
- **Tecla**: "Presiona Enter", "Presiona Tab", "Presiona Escape"
- **Tareas de varios pasos**: "Abre el Explorador de archivos, encuentra el informe y cámbiale el nombre a final.pdf"

### Notas importantes
- **⚠️ Advertencia de uso de API:** Dado que el Operador de IA necesita "ver" exactamente lo que está pasando, envía una captura de pantalla de alta resolución con cada paso. El uso frecuente consumirá tu cuota de API mucho más rápido que las funciones estándar basadas en texto.
- **Aplicaciones de administrador:** Si NVDA no se está ejecutando con privilegios de administrador, es posible que el Operador no pueda interactuar con ventanas que requieren permisos elevados. Esto es una limitación de seguridad de Windows, no un error del complemento.
- **Mejores prácticas:** Para mejores resultados, da comandos claros y específicos. "Haz clic en el botón azul Enviar en la parte inferior del formulario" funcionará casi siempre mejor que simplemente "Haz clic en el botón".

## 4. Análisis de vídeo y audiodescripción

> **Nota:** Las funciones de análisis de vídeo y audiodescripción funcionan exclusivamente con el proveedor **Google Gemini**. Asegúrate de que tu proveedor activo en la configuración del complemento sea Google Gemini.

Vision Assistant Pro introduce potentes capacidades de procesamiento de vídeo diseñadas específicamente para usuarios ciegos. Puede analizar tanto vídeos en línea como grabaciones de pantalla locales para proporcionar descripciones visuales altamente detalladas y generar scripts profesionales de audiodescripción (SRT).

### 4.1 Grabación de pantalla local (Control + V)
Si encuentras un vídeo silencioso, una animación o un tutorial en tu pantalla, puedes capturarlo directamente:
1. Presiona **NVDA + Shift + V** para entrar en la Capa de comandos, luego presiona **Control + V**.
2. El complemento grabará silenciosamente tu pantalla en segundo plano.
3. Presiona **Control + V** de nuevo para detener la grabación.
4. La IA analizará el segmento de vídeo grabado y proporcionará una descripción muy detallada de la escena, los personajes y las acciones.

### 4.2 Análisis de vídeo (Shift + V)
Puedes analizar tanto archivos de vídeo locales como vídeos en línea. Simplemente selecciona un archivo de vídeo local en el Explorador de Windows, o copia un enlace de vídeo en línea al portapapeles. También puedes presionar **Shift + V** en cualquier lugar para abrir un diálogo donde puedes examinar un archivo de vídeo o pegar una URL manualmente.
- **Plataformas en línea compatibles:** YouTube, Instagram, TikTok y Twitter (X).
- La IA detectará automáticamente el archivo local o la URL, procesará el vídeo y proporcionará una descripción visual completa y un resumen de audio.

### 4.3 Generación de audiodescripción (SRT)
Para una experiencia más estructurada, el complemento puede generar scripts profesionales de audiodescripción en formato estándar SubRip (SRT).
- **Temporización inteligente de pausas:** La IA escucha la pista de audio y ancla específicamente sus descripciones visuales a las pausas naturales y los silencios para minimizar inteligentemente la superposición con el diálogo.
- **Seguimiento de personajes:** El motor realiza una pre-pasada para extraer personajes distintos basándose en rasgos faciales inmutables. Construye un diccionario global para rastrear y etiquetar con precisión a los personajes en diferentes escenas sin confundirlos.
- **OCR textual literal:** Cualquier texto que aparezca en pantalla (carteles, teléfonos, créditos) se cita literalmente.
- **Cómo usar:** Para escuchar el subtítulo generado, simplemente coloca el archivo `.srt` en la misma carpeta que tu archivo de vídeo y dale exactamente el mismo nombre. Luego configura tu reproductor multimedia (por ejemplo, VLC o PotPlayer) para enrutar el texto de los subtítulos directamente a tu lector de pantalla o motor TTS durante la reproducción.

### 4.4 Narración de audio sincronizada (exportación a MP3)
Más allá de crear archivos SRT basados en texto, el complemento funciona como una herramienta completa de producción de audiodescripción sintetizando las descripciones en voz y mezclándolas con el vídeo. Al generar un MP3 para archivos de vídeo locales, tienes varios modos de mezcla:
- **AD estándar (mezclar voz):** La narración se superpone directamente sobre el audio del vídeo. Se te preguntará si deseas aplicar **Atenuación de audio** (bajar el volumen de fondo durante las descripciones) para garantizar que la narración sea clara.
- **AD extendida (pausar audio):** El motor pausa el audio original del vídeo durante las descripciones, asegurando que no te pierdas ni una sola palabra del diálogo original ni de la narración de la IA.
- **Vídeos de YouTube:** Para fuentes de YouTube (que no se descargan localmente), la exportación a MP3 contendrá estrictamente la pista de voz de la IA sincronizada sin el audio de fondo del vídeo.

## 5. Lector avanzado de documentos e imágenes

Vision Assistant Pro incluye un Lector de documentos altamente optimizado diseñado para PDFs de varias páginas, imágenes complejas e incluso formatos HEIC de iPhone.

### 5.1 Procesamiento en lotes y reanudación
No necesitas leer un documento extenso de una sola vez. Introduce un rango de páginas (por ejemplo, `1-20`) y la IA procesará todas las páginas en segundo plano. Si NVDA se bloquea o interrumpes el escaneo, el complemento recordará tu progreso y ofrecerá **Reanudar** exactamente donde lo dejaste.

### 5.2 Acción inteligente de archivo
No siempre necesitas abrir el documento primero. En el Explorador de archivos de Windows, simplemente resalta un PDF o imagen y presiona **D** (Lector de documentos) o **F** (Acción inteligente de archivo) dentro de la Capa de comandos. El complemento omitirá instantáneamente el diálogo de archivo y comenzará a procesar el archivo resaltado.

### 5.3 Atajos del visor de documentos
Cuando la ventana del Lector de documentos está abierta, puedes usar los siguientes atajos:
- **Ctrl + AvPág:** Ir a la siguiente página.
- **Ctrl + RePág:** Ir a la página anterior.
- **Alt + A:** Abrir un diálogo de chat para hacer preguntas sobre el documento.
- **Alt + R:** Forzar un **Nuevo escaneo con IA** usando tu proveedor activo.
- **Alt + G:** Generar y guardar un archivo de audio de alta calidad (WAV/MP3). *Oculto si el proveedor no admite TTS.*
- **Alt + S / Ctrl + S:** Guardar el texto extraído como archivo TXT o HTML.

## 6. Etiquetado semántico con IA y Explorador de interfaz

¿Atascado en una aplicación llena de "botones sin etiqueta"? El motor de etiquetado semántico con IA resuelve esto de forma permanente.

### 6.1 Etiquetado permanente de objetos (L)
Enfoca tu lector de pantalla en un gráfico o botón sin etiquetar y presiona **L** en la Capa de comandos. La IA mirará el botón visualmente, determinará su función y aplicará una etiqueta permanente.
*A diferencia de las herramientas de etiquetado de lectores de pantalla más antiguas, este complemento usa un sistema avanzado híbrido de "firma de objeto" (AutomationId/ControlID). ¡Tus etiquetas personalizadas sobrevivirán al redimensionamiento de ventanas, cambio de monitor y actualizaciones de la aplicación!*

### 6.2 Escaneo completo de la aplicación (Shift + L)
Presiona **Shift + L** para escanear toda la ventana activa de una vez. La IA encontrará todos los elementos sin etiquetar y los nombrará inteligentemente de un solo golpe. Luego puedes administrar, renombrar o eliminar en lote estas etiquetas desde el Administrador de etiquetas incorporado.

### 6.3 Explorador de interfaz (E)
¿Necesitas interactuar con un elemento sin navegar hasta él manualmente? Presiona **E** para activar el Explorador de interfaz. La IA escaneará la pantalla y generará una lista accesible de cada elemento en el que se puede hacer clic (ignorando el ruido del sistema como las barras de tareas). Elige un elemento de la lista y el complemento hará clic en él instantáneamente.

## 7. Asistente en vivo

El Asistente en vivo convierte Vision Assistant Pro en un copiloto interactivo en tiempo real.
*(Nota: Esta función es exclusiva de Google Gemini y los proveedores personalizados compatibles con Gemini).*

- **Activación:** Presiona **Control + L** en la Capa de comandos para abrir el diálogo del Asistente en vivo.
- **Interacción en tiempo real:** Habla naturalmente a través de tu micrófono. La IA escuchará tu voz y mirará simultáneamente tu pantalla activa. Puedes hacer preguntas como "¿Qué estoy mirando?" o "Léeme el tercer párrafo."
- **Personalización:** Dentro del diálogo, puedes cambiar el estilo de voz de la IA (por ejemplo, Profesional, Amigable, Animada) y ajustar su "Profundidad de razonamiento" para controlar cuánto razona antes de responder.

## 8. Indicaciones personalizadas y variables

Puedes administrar las indicaciones en **Configuración > Indicaciones > Administrar indicaciones...**.

### Variables compatibles
- `[selection]`: Texto seleccionado actualmente.
- `[clipboard]`: Contenido del portapapeles.
- `[clipboard_image]`: Imagen actualmente en el portapapeles.
- `[screen_obj]`: Captura de pantalla del objeto del navegador.
- `[screen_fg_obj]`: Captura de pantalla de la ventana activa en primer plano.
- `[screen_full]`: Captura de pantalla completa.
- `[file_ocr]`: Seleccionar archivo de imagen/PDF para extracción de texto.
- `[file_read]`: Seleccionar documento para leer (TXT, Código, PDF).
- `[file_audio]`: Seleccionar archivo de audio para análisis (MP3, WAV, OGG).
- `{target_lang}`: Idioma de destino actual.
- `{source_lang}`: Idioma de origen actual.
- `{response_lang}`: Idioma actual de respuesta de la IA.
- `{swap_target}`: Idioma alternativo para traducción con intercambio inteligente.
- `{swap_instruction}`: Bloque de instrucción de traducción con intercambio inteligente.

## 9. Casos de uso reales (¿Qué función debo usar?)

Vision Assistant Pro está repleto de herramientas avanzadas. Aquí tienes algunos escenarios comunes para ayudarte a elegir la correcta:

- **Escenario: Quieres entender el diseño completo de una ventana complicada o una aplicación inaccesible.**
  *Solución:* Presiona **O** (Visión de pantalla completa). La IA analizará toda la pantalla y describirá exactamente dónde están posicionados los elementos, textos y botones.

- **Escenario: Encontraste una imagen en una página web o un gráfico sin etiquetar en un documento.**
  *Solución:* Mueve tu objeto del navegador al gráfico y presiona **V** (Visión de objeto). La IA describirá específicamente qué contiene esa imagen.

- **Escenario: Quieres ver una película o un videoclip con audiodescripción.**
  *Solución:* Presiona **Shift + V** en tu vídeo y elige **"Generar audiodescripción (archivo SRT)"**. Cuando termine, haz clic en **"Generar narración sincronizada (MP3)"** y selecciona **"AD extendida"**. El complemento creará una pista de audio que pausa inteligentemente el diálogo de la película para describir las escenas visuales.

- **Escenario: Encontraste una aplicación llena de "botones sin etiqueta".**
  *Solución:* Presiona **L** para etiquetar permanentemente el botón específico usando IA. O presiona **Shift + L** para escanear y etiquetar toda la ventana de una vez. Si solo quieres hacer clic en algo rápidamente, presiona **E** (Explorador de interfaz) para obtener una lista de todos los elementos en los que se puede hacer clic.

- **Escenario: Necesitas superar un CAPTCHA inaccesible.**
  *Solución:* Presiona **C** (Solucionador de CAPTCHA). La IA capturará automáticamente el CAPTCHA, lo resolverá e inyectará la respuesta en el campo correcto.

- **Escenario: Quieres leer un documento PDF largo de 50 páginas.**
  *Solución:* Presiona **D** (Lector de documentos), configura tu proveedor como Google Gemini e introduce el rango de páginas `1-50`. El complemento extraerá el texto con precisión en segundo plano.

- **Escenario: Estás viendo un tutorial de vídeo silencioso o una animación en tu pantalla.**
  *Solución:* Presiona **Control + V** para comenzar a grabar la pantalla. Deja que el tutorial se reproduzca, luego presiona **Control + V** de nuevo. La IA explicará exactamente lo que se demostró.

***
**Nota:** Se requiere una conexión a Internet activa para todas las funciones de IA. Los documentos de varias páginas se procesan automáticamente.

## 10. Soporte y comunidad

Mantente actualizado con las últimas noticias, funciones y lanzamientos:
- **Canal de Telegram:** [t.me/VisionAssistantPro](https://t.me/VisionAssistantPro)
- **GitHub Issues:** Para informes de errores y solicitudes de funciones.

## 11. Colaboradores del proyecto

Un agradecimiento de corazón a los miembros de nuestra comunidad que apoyan el desarrollo continuo y el mantenimiento de este proyecto con sus generosas contribuciones económicas:

*   **@Alyabani94**
*   **Ali Alamri**
*   **Ilya**
*   **Colaborador anónimo** (`UQDd...CnMY`)
*   **leonardo0216**
*   **Sergei Fleytin**
*   **Suman Gayen**

*Si deseas apoyar el proyecto económicamente y ver tu nombre aquí, puedes encontrar la opción **Donar** en el menú Herramientas de NVDA (submenú Vision Assistant) o durante el proceso de configuración después de la instalación.*

---
## Cambios para 2026.07.15

*   **Filtrado inteligente de modelos de API**: Revisión completa del sistema de filtrado de modelos para usar un enfoque de lista negra pura en lugar de listas blancas. Se añadieron palabras clave de filtrado más potentes (`embedding`, `bison`, `gecko`, `audio`, `realtime`, `babbage`, `moderation`, `deep`, `antigravity`, `computer`) para garantizar que el desplegable del modelo de chat principal permanezca perfectamente limpio y preparado para el futuro, mientras que todos los modelos especializados siguen siendo accesibles en la sección de Enrutamiento avanzado.
*   **Búsqueda en enrutamiento avanzado**: Todos los desplegables de Enrutamiento avanzado de modelos (OCR, STT, TTS, Operador, Vídeo, En vivo) y el selector de variante de eSpeak son ahora completamente buscables. Puedes escribir rápidamente para filtrar y encontrar tu modelo o variante deseados.
*   **Nuevos atajos de capa de comandos**:
    *   **Configuración (`Alt + S`)**: Abre directamente el diálogo de configuración de Vision Assistant Pro.
    *   **Informe de claves con cuota agotada (`Alt + Q`)**: Informa sobre el número exacto de claves API de Gemini que han superado su cuota diaria, identificando en qué modelo específico están agotadas, y anuncia su hora exacta de restablecimiento.
    *   **Auditoría de enrutamiento (`Alt + M`)**: Audita y anuncia tu configuración actual de Enrutamiento avanzado, leyendo qué modelos están activamente seleccionados para tareas especializadas (omitiendo la configuración predeterminada).
*   **Revisión completa del Analizador de vídeo**: ¡El Analizador de vídeo ha sido completamente transformado! Anteriormente, solo proporcionaba una descripción básica de los vídeos en línea. Ahora es una suite completa de procesamiento de vídeo diseñada para usuarios ciegos:
    *   **Grabación de pantalla local (`Control+V`)**: Ahora puedes grabar vídeos silenciosos directamente desde tu pantalla. La IA analizará el segmento grabado y proporcionará una descripción muy detallada de la escena, el diseño y las acciones.
    *   **Generación de audiodescripción (SRT)**: El complemento ahora puede generar scripts de audiodescripción muy detallados (en formato SRT estándar) para vídeos, con temporización inteligente de pausas para anclar las descripciones a los silencios naturales de la pista de audio, y OCR literal para cualquier texto en pantalla.
    *   **Narración de audio sincronizada (exportación a MP3)**: Más allá de los subtítulos basados en texto, el complemento puede sintetizar la audiodescripción en voz, mezclarla automáticamente con la pista de audio original del vídeo, aplicar atenuación de audio (bajando el volumen de fondo durante las descripciones) y exportar el resultado sincronizado final como un archivo MP3.
    *   **Acción inteligente de archivo de vídeo**: Si te enfocas en un archivo de vídeo local y presionas el atajo de vídeo, el complemento lo detectará automáticamente y procesará el archivo directamente.
    *   **Seguimiento avanzado de personajes**: La IA ahora realiza una pre-pasada de extracción de personajes. Construye un diccionario global de personajes y los rastrea con precisión segmento por segmento sin confundir identidades.
    *   **Configuración de análisis de vídeo**: Se añadieron nuevas opciones para controlar los tamaños de fragmentos SRT, los subtítulos de personajes y los avisos.
    *   **Enrutamiento de modelos ampliado**: Ahora puedes seleccionar explícitamente modelos de vídeo especializados (`gemini_video_model`, `custom_video_model`) en la configuración de Enrutamiento avanzado de modelos.
*   **Gestión inteligente de cuotas de API**: Se mejoró el manejo de errores 429 (Límite diario) rastreando las cuotas por modelo. Si una clave alcanza su límite diario en un modelo, se pone en cuarentena inteligentemente solo para ese modelo, dejando la clave disponible para su uso con otros modelos.

## Cambios para 7.0.0

*   **Reanudación de escaneos no finalizados**: Se añadió una función para reanudar tanto el Lector de documentos como las Acciones inteligentes de archivo. Si un escaneo se interrumpe, ahora puedes continuar desde donde se detuvo en lugar de empezar desde cero.
*   **Nueva variable `[screen_fg_obj]`**: Se añadió una variable de indicación personalizada para capturar una captura de pantalla solo de la ventana activa en primer plano, en lugar de toda la pantalla.
*   **Reintentos inteligentes y rotación de claves**: El complemento ahora reintenta silenciosamente hasta 5 veces con la misma clave ante sobrecargas temporales del servidor. Si los reintentos fallan, cambia automáticamente a la siguiente clave API de la lista.
*   **Detección de cortina de pantalla**: Se añadió una verificación para evitar tomar capturas de pantalla cuando la Cortina de pantalla está activa. Avisará y se detendrá, evitando enviar imágenes negras y desperdiciar tokens de API.
*   **Ajustes del Lector de documentos**: El diálogo de rango PDF ahora preselecciona automáticamente el idioma de destino predeterminado. También se mejoró el manejo de hilos para que las tareas en segundo plano se detengan correctamente al cerrar el lector.
*   **Integración OCR nativa de Mistral**: Se integró la API OCR de documentos nativa de Mistral con procesamiento en lotes usando el punto de acceso especializado `/v1/ocr`.
*   **Controladores de URL personalizados dinámicos**: Modificar la URL de API personalizada ahora borra instantáneamente la lista de modelos en caché y restaura el cuadro de texto de entrada manual del modelo.
*   **Motor de entrada del Operador de IA renovado**: Se reemplazó la API `mouse_event` con la moderna API `SendInput` de Windows, aportando mayor compatibilidad con aplicaciones modernas y pantallas de alta resolución.
*   **Arrastrar y soltar corregido**: Las operaciones de arrastrar y soltar en el Operador de IA son ahora completamente estables.
*   **Soporte multimonitor**: El Operador de IA ahora funciona correctamente en configuraciones de varios monitores.
*   **Simulación de teclado mejorada**: Soporte completo para teclas extendidas (flechas, Inicio, Fin, Re Pág/Av Pág, Insertar, Suprimir, F1-F12).
*   **Soporte de imágenes HEIC/HEIF**: Compatibilidad nativa con formatos de foto de iPhone. Puedes seleccionar archivos `.heic` y `.heif` directamente.

## Cambios para 6.5.0

*   **Asistente en vivo**: Se añadió una función de asistente de voz y pantalla en tiempo real, disponible exclusivamente para el proveedor Google Gemini (o proveedores personalizados compatibles con Gemini). Incluye personalización interactiva de voz y profundidad de razonamiento directamente dentro del diálogo, con reconexión automática al cambiar la configuración.
*   **Proveedor de IA MiniMax**: Se integró MiniMax como proveedor par con soporte multimodal completo (chat, visión, OCR), TTS personalizado con más de 300 voces dinámicas y eliminación automática de bloques de razonamiento (por ejemplo, `<think>...</think>`) de las salidas.
*   **Traducción del visor de documentos**: Se corrigió un error de traducción silencioso para usuarios de NVDA que no usan inglés, asegurando que se envíe el código de idioma estándar de 2 letras a Google Translate en lugar del nombre del idioma localizado.
*   **Reintento de escaneo en lotes de PDF**: Se implementó una lógica de reintento altamente optimizada, separada y silenciosa para el escaneo en lotes de documentos PDF.
*   **Estado del visor de documentos**: Se corrigió un error donde el estado general del complemento permanecía bloqueado en "Procesamiento por lotes iniciado" durante escaneos de documentos largos.
*   **Fallo de hilo resuelto**: Se corrigió un fallo grave de aserción de hilo `IsMain() failed in wxTimerImpl` al abrir documentos desde un hilo de fondo.

## Cambios para 6.1.2

*   **Verificación previa de etiquetas duplicadas**: Se corrigió un problema en el etiquetado individual donde la verificación de duplicados usaba claves de coordenadas antiguas.
*   **Chat de documentos para proveedores que no son Gemini**: Se corrigió una verificación estricta de clave API en el chat de documentos para garantizar que los usuarios de OpenAI, Groq o proveedores personalizados locales puedan chatear con documentos sin ser bloqueados.
*   **Traducción rápida de OCR de Chrome**: Se restauró la API de traducción gratuita y sin clave para el OCR de Chrome.
*   **Filtro alfanumérico de CAPTCHA**: Se corrigió la lógica de filtrado en el solucionador de CAPTCHA.
*   **Actualización de ayuda de la capa de comandos**: Se corrigió el atajo de anuncio de estado en el menú de ayuda de `L` a `I`.

## Cambios para 6.1.1

*   **Corrección de salida de Gemma 4 Thinking**: Se corrigió un problema con los modelos Gemma 4 donde todo el proceso de pensamiento interno se mostraba como respuesta final.
*   **OCR en lotes desde el Explorador de archivos**: Ahora puedes seleccionar múltiples fotos o PDFs directamente en el Explorador de archivos de Windows y extraer texto o analizarlos en lotes.

## Cambios para 6.1.0

*   **Integración universal de IA local (Configurar IA local)**: Se añadió un nuevo botón **"Configurar IA local"** en la configuración del proveedor personalizado para **Ollama**, **LM Studio**, **Jan.ai** y **KoboldCPP**.
*   **Omisión inteligente de proxy local**: Se reconstruyó la lógica de conexión con un mecanismo avanzado de omisión de proxy.
*   **Etiquetado de IA ultraestable (v2)**: Sistema avanzado e híbrido de **firma de objeto** basado en UIA **AutomationId** o Win32 **ControlID**.
*   **Migración automática perfecta de etiquetas**: Migración transparente de etiquetas antiguas al nuevo formato de huella digital estable.

## Cambios para 6.0

*   **Introducción al etiquetado semántico con IA**: Etiquetado permanente de botones e iconos sin nombre. Presiona **L** para el objeto actual o **Shift+L** para escanear toda la aplicación.
*   **Gestión inteligente de etiquetas**: Nuevo administrador de etiquetas completamente accesible.
*   **Análisis directo de archivos**: El complemento detecta si estás enfocado en un PDF o imagen en el Explorador de archivos y lo procesa directamente.

## Cambios para 5.6

*   **Motor OCR "Ninguno (Extraer capa de texto)" añadido**: Extrae texto directamente de PDFs con capacidad de búsqueda sin usar créditos de IA.
*   **Precisión mejorada del Explorador de interfaz**: Mejor identificación de tipos de elementos y estados.
*   **Recordatorio de configuración de instalación**: Notificación después de la instalación para guiar a los usuarios al menú de configuración.

## Cambios para 5.5.2

*   **Error de escritura del Operador de IA corregido:** Se resolvió un error donde se escribía la letra 'v' en lugar de pegar texto.
*   **Estabilidad mejorada:** Manejo robusto de errores para las operaciones del portapapeles.
*   **Optimización de temporización:** Ajuste de los retrasos internos para eventos de teclado.

## Cambios para 5.5 (La actualización de automatización)

*   **Operador de IA (Control autónomo - Shift+A):** Vision Assistant Pro ahora toma el control de tu PC mediante comandos en lenguaje natural.
*   **Explorador visual de interfaz (E):** Lista de todos los elementos en los que se puede hacer clic en la ventana activa.
*   **Acción inteligente de archivo contextual (F):** Pregunta de forma inteligente si deseas descripción visual u OCR al seleccionar una imagen.
*   **Optimización del núcleo:** Limpieza profunda de la lógica interna del complemento.

## Cambios para 5.0

* **Arquitectura multiproveedor**: Soporte completo para **OpenAI**, **Groq** y **Mistral** junto a Google Gemini.
* **Enrutamiento avanzado de modelos**: Selección de modelos específicos por tarea (OCR, STT, TTS).
* **Configuración avanzada de punto de acceso**: Control granular sobre servidores locales o de terceros.
* **Visibilidad inteligente de funciones**: Oculta automáticamente las funciones no compatibles según el proveedor.
* **Obtención dinámica de modelos**: Obtiene la lista de modelos directamente desde la API del proveedor.
* **OCR y traducción híbridos**: Google Translate para OCR de Chrome, traducción con IA para Gemini/Groq/OpenAI.
* **"Nuevo escaneo con IA" universal**: Utiliza cualquier proveedor de IA activo para reprocesar páginas.

## Cambios para 4.6
* **Recuperación interactiva de resultados:** Tecla **Espacio** en la capa de comandos para reabrir la última respuesta de IA.
* **Centro de comunidad en Telegram:** Enlace al canal oficial en el menú Herramientas de NVDA.
* **Estabilidad de respuesta mejorada:** Lógica central optimizada para Traducción, OCR y Visión.
* **Guía de interfaz mejorada:** Descripciones de configuración actualizadas.

## Cambios para 4.5
* **Administrador avanzado de indicaciones:** Diálogo de gestión dedicado en configuración.
* **Soporte de proxy completo:** Configuración de proxy aplicada a todas las solicitudes de API.
* **Migración automática de datos:** Sistema de migración inteligente al formato JSON v2.
* **Compatibilidad actualizada (2025.1):** Versión mínima requerida de NVDA: 2025.1.
* **Interfaz de configuración optimizada:** Gestión de indicaciones en un diálogo separado.
* **Guía de variables de indicaciones:** Guía integrada para variables dinámicas.

## Cambios para 4.0.3
*   **Mayor resiliencia de red:** Mecanismo de reintento automático.
*   **Diálogo visual de traducción:** Ventana dedicada para resultados de traducción.
*   **Vista formateada agregada:** Todas las páginas procesadas en una sola ventana organizada.
*   **Flujo de trabajo OCR optimizado:** Omite la selección de rango para documentos de una sola página.
*   **Estabilidad de API mejorada:** Autenticación basada en encabezados más robusta.
*   **Correcciones de errores:** Varios fallos potenciales resueltos.

## Cambios para 4.0.1
*   **Lector de documentos avanzado:** Visor para PDF e imágenes con selección de rango de páginas y navegación fluida.
*   **Nuevo submenú de herramientas:** Submenú "Vision Assistant" en el menú Herramientas de NVDA.
*   **Personalización flexible:** Elección de motor OCR y voz TTS desde el panel de configuración.
*   **Soporte de múltiples claves API:** Varias claves API de Gemini.
*   **Motor OCR alternativo:** Nuevo motor OCR para límites de cuota de la API de Gemini.
*   **Rotación inteligente de claves API:** Cambia automáticamente a la clave más rápida.
*   **Documento a MP3/WAV:** Generación de audio de alta calidad directamente dentro del lector.
*   **Soporte de historias de Instagram:** Descripción y análisis de Historias de Instagram.
*   **Soporte de TikTok:** Descripción visual y transcripción de audio de vídeos de TikTok.
*   **Diálogo de actualización rediseñado:** Interfaz accesible con cuadro de texto desplazable.
*   **Estado y experiencia de usuario unificados:** Diálogos de archivos estandarizados.

## Cambios para 3.6.0
*   **Sistema de ayuda:** Comando de ayuda (`H`) dentro de la capa de comandos.
*   **Análisis de vídeos en línea:** Soporte ampliado para vídeos de **Twitter (X)**.
*   **Contribución al proyecto:** Diálogo de donación opcional.

## Cambios para 3.5.0
\*   \*\*Capa de comandos:\*\* Sistema de capa de comandos (`NVDA+Shift+V`) para agrupar los atajos bajo una sola tecla maestra.
\*   \*\*Análisis de vídeos en línea:\*\* Nueva función para analizar vídeos de YouTube e Instagram directamente por URL.

## Cambios para 3.1.0
*   **Modo de salida directa:** Opción para escuchar las respuestas de IA directamente sin abrir una ventana de chat.
*   **Integración con portapapeles:** Copiar automáticamente las respuestas de IA al portapapeles.

## Cambios para 3.0

*   **Nuevos idiomas:** Traducciones al **persa** y **vietnamita**.
*   **Modelos de IA ampliados:** Lista de modelos reorganizada con prefijos claros (`[Gratis]`, `[Pro]`, `[Auto]`). Soporte para **Gemini 3.0 Pro** y **Gemini 2.0 Flash Lite**.
*   **Estabilidad del dictado:** Verificación de seguridad para ignorar clips de audio de menos de 1 segundo.
*   **Gestión de archivos:** Corrección para carga de archivos con nombres no ingleses.
*   **Optimización de indicaciones:** Lógica de traducción mejorada y resultados de Visión estructurados.

## Cambios para 2.9

*   **Traducciones al francés y turco añadidas.**
*   **Vista formateada:** Botón "Ver formateado" en los diálogos de chat.
*   **Configuración de Markdown:** Nueva opción "Limpiar Markdown en el chat" en la Configuración.
*   **Gestión de diálogos:** Corrección para ventanas que se abrían varias veces.
*   **Mejoras de experiencia de usuario:** Títulos de diálogos de archivos estandarizados.

## Cambios para 2.8
* Traducción al italiano añadida.
* **Informe de estado:** Nuevo comando (NVDA+Control+Shift+I) para anunciar el estado actual.
* **Exportación HTML:** Botón "Guardar contenido" ahora guarda como HTML formateado.
* **Interfaz de configuración:** Diseño mejorado del panel de configuración.
* **Nuevos modelos:** Soporte para gemini-flash-latest y gemini-flash-lite-latest.
* **Idiomas:** Nepalí añadido a los idiomas compatibles.
* **Lógica del menú Refinar:** Corrección de error crítico para idiomas distintos al inglés.
* **Dictado:** Mejora de la detección de silencio.
* **Configuración de actualizaciones:** "Buscar actualizaciones al iniciar" deshabilitado por defecto.
* Limpieza de código.

## Cambios para 2.7
* Estructura del proyecto migrada a la plantilla oficial de complementos de NV Access.
* Lógica de reintento automático para errores HTTP 429 (Límite de velocidad).
* Indicaciones de traducción optimizadas para mayor precisión.
* Traducción al ruso actualizada.

## Cambios para 2.6
* Soporte de traducción al ruso añadido (Gracias a nvda-ru).
* Mensajes de error actualizados con comentarios más descriptivos sobre la conectividad.
* Idioma de destino predeterminado cambiado al inglés.

## Cambios para 2.5
* Comando de OCR de archivos nativo añadido (NVDA+Control+Shift+F).
* Botón "Guardar chat" añadido a los diálogos de resultados.
* Soporte completo de localización (i18n) implementado.
* Retroalimentación de audio migrada al módulo de tonos nativo de NVDA.
* Cambiado a la API de archivos de Gemini para mejor manejo de archivos PDF y de audio.
* Corrección del fallo al traducir texto que contiene llaves.

## Cambios para 2.1.1
* Corrección donde la variable [file_ocr] no funcionaba correctamente dentro de las Indicaciones personalizadas.

## Cambios para 2.1
* Todos los atajos estandarizados para usar NVDA+Control+Shift, eliminando conflictos con el diseño de portátil de NVDA.

## Cambios para 2.0
* Sistema de actualización automática incorporado implementado.
* Caché de traducción inteligente añadida para recuperación instantánea de textos traducidos previamente.
* Memoria de conversación añadida para refinar contextualmente los resultados en los diálogos de chat.
* Comando dedicado de traducción del portapapeles añadido (NVDA+Control+Shift+Y).
* Indicaciones de IA optimizadas para aplicar estrictamente la salida en el idioma de destino.
* Corrección del fallo causado por caracteres especiales en el texto de entrada.

## Cambios para 1.5
* Soporte añadido para más de 20 nuevos idiomas.
* Diálogo interactivo de refinado implementado para preguntas de seguimiento.
* Función de Dictado inteligente nativo añadida.
* Categoría "Vision Assistant" añadida al diálogo de Gestos de entrada de NVDA.
* Corrección de fallos de COMError en aplicaciones específicas como Firefox y Word.
* Mecanismo de reintento automático para errores del servidor añadido.

## Cambios para 1.0
* Lanzamiento inicial.
