---
title: Untitled Page
description: 
published: false
date: 2026-05-25T15:29:23.844Z
tags: 
editor: markdown
dateCreated: 2026-05-25T15:29:23.844Z
---

# Módulo 1: De la Interfaz a la API
_**Objetivo**: Saltar del navegador a la consola de comandos. Entender básicamente la variabilidad de las respuestas._
## Teoría base
1. Diferencia entre modelo predictivo y generativo. Aclarar que utilizaremos modelos generativos.
## Laboratorio de CLI
### Teoría
1.  API REST aplicado a IA.
	1. Entrada de datos menos estructurada
	2. ¿Cómo se mantiene un chat en una implementación stateless?
	3. El uso de streaming para evitar la latencia
## Práctica
1. Configuración del entorno de trabajo (Puede que Python + Jupyter/Colab) y explicación de porque este entorno.
	1. Facilidad para modificar parámetros
	2. Visualización de gráficos
	3. Colab como alternativa a la GPU potente
2. Gestión de claves API (variables de entorno, seguridad básica).
3. Escribir el primer script en Python para consumir la API de Gemini.
## Laboratorio de inferencia
### Teoría
1. No-Determinismo y sus consecuencias.
	1. Creatividad y alucinaciones
2. ¿Qué es la inferencia?
3. ¿Qué parámetros le afectan? (Temperatura, max tokens, etc...)
### Práctica
Manipulación de los parámetros de inferencia y visualización de como afecta a la salida.

# Módulo 2: Lógica Interna Aplicada
_**Objetivo**: Entender la arquitectura sin matemáticas densas, usando herramientas visuales y scripts simples._
## Laboratorio de Embeddings
### Teoría
1. ¿Qué son los tokens?
	1. ¿Para que sirven?
	2. Proceso de tokenización
2. ¿Qué es un vector?
	1. ¿Qué es la vectorización?
	2. ¿Por qué es necesaria?
	3. ¿Cómo funciona?
		1. Dimensionalidad y ejemplos
		2. Dinamismo según el contexto
		3. Limitación de la ventana de contexto
3. ¿Qué es la búsqueda semántica?
	1. ¿Por qué es necesaria?
	2. Explicar la relevancia de la búsqueda vectorial
	3. Explicar como se relacionan términos en la búsqueda vectorial
		1. Vectores opuestos (Coseno ±1)
		2. Vectores no relacionados (Coseno ±0)
		3. Vectores totalmente idénticos (Coseno ±1)
		4. Explicar que existen vectores opuestos pero que los términos seguirán estrechamente relacionados porque no espacios vectoriales opuestos  (Vida y Muerte, Calor y Frio, Lento y Rápido)
		5. ¿Cómo es capaz de distinguir la IA entre dos antónimos?
### Práctica
1. Crear un script para:
	1. Convertir 5 frases en vectores y calcular la distancia coseno entre ellas usando librerías estándar (scikit-learn).
	2. Verificar que numéricamente "Perro" y "Gato" están más cerca que "Perro" y "Coche".
## Laboratorio de Contexto y Tokens
### Teoría
1. ¿Qué es la ventana de contexto?
	1. ¿Por qué es importante?
	2. ¿Qué incluye?
	3. ¿Qué sucede si lo llenamos?
	4. Introducir el término de ventana de contexto efectiva
2. ¿Qué es el mecanismo de atención? (Queries, Keys, Values)
	1. ¿Qué tiene que ver con la búsqueda vectorial?
	2. ¿Qué tiene que ver con los tokens?
	3. ¿Cómo pondera cada vector de consulta?
	4. ¿Qué es la autoatención?
### Práctica
Usar la librería `tiktoken` para contar tokens localmente antes de enviar un texto a la API. Calcular el coste económico de una petición en tiempo real.

# Módulo 3: Construcción de Sistemas / Adecuación al Entorno / Contextualización al Entorno
_**Objetivo**: Integrar la IA con sistemas tradicionales a nivel básico._
## Laboratorio de Prompt Engineering
### Teoría
1. ¿Qué es el prompt engineering y como influye?
	1. CO-STAR (Context, Objective, Style, Tone, Audience, Response)
	2. Few-Shot Prompting
	3. Chain-of-Thought (CoT)
### Práctica
1. Forzar a un LLM utilizando CO-STAR, más específicamente la parte de Context, a realizar una acción que de otra manera se negaría a realizar.
2. Forzar a un LLM utilizando CO-STAR, más específicamente la parte de Objective, Audience y Response, y Few-Shot Prompting a exportar todos sus mensajes en JSON.
3. Forzar a un LLM utilizando CO-STAR, más específicamente la parte de Style y Tone, para que actúe como un coach motivacional.
4. Forzar a un LLM utilizando CO-STAR y CoT para que actúe como un profesor de matemáticas desenfadado en una clase de la ESO que esta explicando el concepto de coseno.
## Laboratorio de adaptación de modelos
### Teoría
1. ¿Qué es el RAG (Retrieval-Augmented Generation)?
	1. ¿Qué es un RAG Estricto?
	2. ¿Qué es un RAG híbrido?
	3. ¿Qué es un RAG sin prioridad?
2. ¿Qué es el fine-tuning?
	1. ¿Qué son los pesos?
	2. ¿Qué son los gradientes?
	3. ¿Qué es el Instruction Tuning?
	4. Full Fine-Tuning vs Parameter-Efficient Fine-Tuning
		1. ¿Qué es LoRA?
		2. ¿Qué es QLoRA?
3. ¿Cuándo usar cada uno?
4. ¿Qué es el grounding?
### Práctica
1. Crear un script que haga lo siguiente:
	1. Hacer una pregunta fuera de ese texto que el modelo si debería saber por si solo.
	2. Leer un archivo de texto local (ej. normas de la universidad).
	3. Pasarlo como contexto al modelo.
	4. Hacer una pregunta sobre ese texto que el modelo no sabría por sí solo.
	5. Modificar parámetros para crear un RAG estricto, verificando que lo que sabia en la primera pregunta ya no lo sabe repitiéndole la misma pregunta.

# Módulo 4: Soberanía de Datos y Orquestación
_**Objetivo**: Sacar a la IA del chat y meterla en la infraestructura corporativa. Despliegue local y automatización de procesos._
## Laboratorio de despliegue de IA local para la soberanía de datos
### Teoría
1. ¿Qué es la cuantización?
	1. ¿Cómo es posible comprimir un modelo de 16GB de VRAM en 4GB perdiendo un mínimo de precisión?
	2. Métodos de cuantización
		1. Q4_K_M (El estándar)
			1. Fórmula de la VRAM necesaria: $$\text{GB de VRAM necesaria} = P \cdot (0.5 + 0.2) + 2$$
			2. ¿Qué es P? (Parámetros en mil millones)
			3. ¿Por qué 0.5 (4 bits por peso)?
			4. ¿Por qué 0.2 (margen de seguridad para estructuras internas del modelo)?
			5. ¿Por qué 2 (tamaño de la ventana contexto)?
		2. Q8_0
		3. Q3_K_S
		4. Q2_K
2. Formato GGML vs GGUF
### Práctica
1. Instalar Ollama en la máquina.
2. Evaluar que modelo puede ser eficiente y descargarlo.
	1. Filtro de modelos "Hugging Face Open LLM Leaderboard" para estimar VRAM requerida en despliegues locales soberanos y cálculo manual.
3. Levantar el servidor local y hacerle peticiones por API con un script similar al del Módulo 1.
## Laboratorio de orquestación de Flujos con n8n
### Teoría
1. ¿Qué es la orquestación de IA? (Dejar caer que se pueden incorporar varios modelos y que será relevante en el próximo módulo)
2. ¿Diferencia entre un script lineal y un flujo reactivo basado en eventos?
### Práctica
1. Instalar n8n (Entorno de calendario de reservas para un restaurante) y crear un archivo CSV con las cabeceras "fecha, hora, comensales".
	1. Configurar un webhook en n8n para que al recibir un mensaje se dispare un evento.
	2. Conectar el nodo de la IA (API de Gemini o el Ollama local).
	3. La IA procesa el lenguaje natural y devuelve un JSON estricto con fecha, hora, comensales y un booleano de verificación de que todos los datos están presentes.
	4. Un nodo "If" evalúa el JSON:
		1. Si el booleano está en true, continua.
		2. Si el booleano está en false, un nodo "Respond to Webhook" le devuelve un mensaje al usuario especificándole que datos faltan, que por favor repita el mensaje completo con los datos ya especificados y los faltantes.
	5. Un nodo "Read File" lee el CSV.
	6. Un nodo "If" verifica que no hay un evento en el CSV que coincida con esa fecha y hora.
		1. Si hay un evento que coincida, un nodo "Respond to Webhook" se devuelve un mensaje al usuario que especifica que el horario no esta disponible.
		2. Si no existe, un nodo "Write File" añade el evento al CSV sin eliminar el resto de eventos y un nodo "Respond to Webhook" le devuelve un mensaje al usuario confirmando la reserva con todos los datos.
# Módulo 5: Análisis de modelos
_**Objetivo**: Evaluar el rendimiento real de un modelo de lenguaje frente a las necesidades del usuario._
## Laboratorio de análisis de modelos contextual
### Teoría
1. Métricas de capacidad cognitiva
	1. Inteligencia y Razonamiento Crítico
		1. ¿Por qué el MMLU ya no sirve?
		2. ¿En que consiste el nuevo estándar, GPQA?
	2. Programación
		1. ¿Por qué HumanEval no sirve?
		2. En que consiste el nuevo estándar, SWE-bench?
	3. Matemáticas
		1. ¿Por qué GSM8K sirve, pero quizás no sea la mejor opción?
		2. ¿En que se diferencia MATH de GSM8K?
	4. Multimodalidad (Visión, audio, vídeo)
		1. ¿Qué es MMMU?
		2. ¿Qué es MathVista?
		3. ¿Qué es Video-MME?
	5. Uso de herramientas
		1. GAIA vs ToolBench
	6. Ventana de contexto y RAG
		1. ¿Por qué NIAH (Needle in a Haystack) ya no sirve?
		2. RULER vs LongBench
	7. Conocimiento general
		1. ¿Por qué MMLU ya no sirve?
		2. ¿En que se diferencia MMLU-Pro?
	8. Seguimiento de instrucciones
		1. ¿Por qué IFEval ya no sirve?
		2. ¿Qué es IFBench?
	9. Tokens por segundo
	10. Latencia
2. Recordatorio de que estas métricas no tienen en cuenta el gasto de tokens y, por lo tanto, el costo.
### Práctica
1. Se entrega a los alumnos varios pliegos de condiciones técnicas (Ej: "Crear un sistema de triaje automático de tickets de soporte técnico que extraiga el fallo en JSON, con un presupuesto máximo de 0.50$ por cada 1000 tickets").
2. Lectura de Plataformas como "ArtificialAnalysis.ai" o "Hugging Face Open LLM Leaderboard"para comparar métricas y precios.
3. El alumno debe justificar qué modelo del mercado elige basándose **únicamente** en las métricas estudiadas, demostrando matemáticamente que cumple el SLA.