# Guía del Proyecto y Estructura LaTeX

Este repositorio contiene la estructura modular y la configuración de estilos para el informe técnico:
**"Diseño e implementación de un sistema IoT para contenedores municipales utilizando tecnología LoRa P2P en la manzana del Mercado San Camilo, Arequipa"**.

El documento ha sido diseñado siguiendo estándares formales de presentación, utilizando una paleta de colores premium y bloques de contenido interactivos.

---

## 📁 Estructura del Proyecto

El proyecto está organizado de manera modular para facilitar la edición colaborativa y el orden:

```text
├── main.tex                    # Archivo raíz principal (compila el documento)
├── referencias.bib             # Base de datos de bibliografía (formato BibLaTeX)
├── .gitignore                  # Exclusiones de archivos auxiliares y compilados
├── README.md                   # Esta guía de trabajo
│
├── config/                     # Configuraciones generales de LaTeX
│   ├── packages.tex            # Carga de paquetes y librerías externas
│   ├── metadata.tex            # Datos editables (Título, autor, docente, etc.)
│   ├── styles.tex              # Definición de colores, márgenes, tipografía y diseño
│   └── macros.tex              # Comandos personalizados y cajas (tcolorbox)
│
├── frontmatter/                # Páginas preliminares
│   ├── portada.tex             # Estilo y distribución de la carátula
│   └── resumen.tex             # Resumen y palabras clave
│
├── sections/                   # Capítulos del cuerpo del informe
│   ├── 01_introduccion.tex     # Introducción, justificación y problemática
│   ├── 02_objetivos.tex        # Objetivos generales y específicos
│   ├── 03_fundamento_teorico.tex # Marco teórico y conceptos clave
│   ├── 04_metodologia_ansys.tex # Configuración de simulación y metodología
│   ├── 05_resultados.tex       # Presentación de resultados y simulaciones
│   ├── 06_discusion.tex        # Discusión de los resultados obtenidos
│   └── 07_conclusiones.tex     # Conclusiones y trabajos futuros
│
├── appendices/                 # Anexos
│   └── anexo_a.tex             # Material complementario o códigos fuente
│
└── figures/                    # Recursos gráficos e imágenes del informe
    ├── logo.png                # Logotipo institucional para la portada
    ├── captura_placeholder.png  # Imagen de muestra para metodología
    └── resultado_placeholder.png # Imagen de muestra para resultados
```

---

## 🛠️ Cómo Trabajar en el Proyecto

### 1. Configuración de Datos Personales
Edita únicamente el archivo [metadata.tex](file:///e:/ING%20DE%20TELECOMUNICACIONES/PROYECTOS/PROYECTO%20FINAL/INFORME/GUIA%20POR%20DOCENTE/BORRADOR%201.0/config/metadata.tex) para personalizar la información general:
* Universidad, Facultad y Escuela.
* Título y subtítulo del informe.
* Nombre del docente y del curso.
* Nombre, código y grupo de los autores.

### 2. Escritura de Capítulos
Cada capítulo del informe está separado en un archivo `.tex` dentro de la carpeta [sections/](file:///e:/ING%20DE%20TELECOMUNICACIONES/PROYECTOS/PROYECTO%20FINAL/INFORME/GUIA%20POR%20DOCENTE/BORRADOR%201.0/sections). Puedes editarlos directamente. Para crear subsecciones estructuradas, utiliza:
```latex
\section{Nombre de la Sección}
\subsection{Subsección}
\subsubsection{Detalle específico}
```

### 3. Inserción de Imágenes y Capturas
En lugar de escribir todo el entorno tradicional de `figure`, se ha provisto una macro simplificada llamada `\captura` en [macros.tex](file:///e:/ING%20DE%20TELECOMUNICACIONES/PROYECTOS/PROYECTO%20FINAL/INFORME/GUIA%20POR%20DOCENTE/BORRADOR%201.0/config/macros.tex):
```latex
\captura[ancho]{ruta/de/la/imagen.png}{Título o descripción de la figura}
```
* **Ejemplo de uso:** `\captura[0.85]{figures/logo.png}{Logotipo oficial de la universidad.}` *(El ancho por defecto es 0.88 de la línea de texto)*.

### 4. Uso de Cajas Modernas y Semánticas
Para resaltar partes importantes del documento, utiliza las siguientes cajas de contenido personalizadas:
* **Información General:**
  ```latex
  \begin{infobox}
      Texto explicativo o información general complementaria.
  \end{infobox}
  ```
* **Notas de Simulación:**
  ```latex
  \begin{warningbox}
      Detalles críticos sobre la simulación en ANSYS o advertencias técnicas.
  \end{warningbox}
  ```
* **Resultados Clave:**
  ```latex
  \begin{resultbox}
      Conclusiones y datos de salida de gran relevancia obtenidos de la simulación.
  \end{resultbox}
  ```
* **Tarjetas Conceptual/Teóricas:**
  ```latex
  \begin{conceptcard}{Nombre del Concepto}
      Definición concisa o fórmulas principales.
  \end{conceptcard}
  ```
* **Bloques de Código Estilo Editor:**
  ```latex
  \begin{codeeditor}{NombreArchivo.py}
  \begin{lstlisting}[language=Python]
  # Código aquí
  print("Hola Mundo")
  \end{lstlisting}
  \end{codeeditor}
  ```

### 5. Códigos QR Vectoriales Interactivos
Si quieres enlazar hojas de datos, repositorios de código o videos de simulación, usa la macro `\enlaceQR`:
```latex
\enlaceQR[tamaño_qr]{url}{Título del Enlace}{Breve descripción explicativa}
```
* **Ejemplo:** `\enlaceQR{https://github.com}{Repositorio GitHub}{Acceso al código fuente del firmware del microcontrolador.}`

### 6. Gestión de Referencias Bibliográficas
1. Añade tus entradas bibliográficas en formato BibTeX en el archivo [referencias.bib](file:///e:/ING%20DE%20TELECOMUNICACIONES/PROYECTOS/PROYECTO%20FINAL/INFORME/GUIA%20POR%20DOCENTE/BORRADOR%201.0/referencias.bib).
2. Cítalas en el texto usando el comando `\cite{id_referencia}`.
3. El documento las formateará automáticamente bajo la norma **IEEE**.

---

## 🚀 Compilación del Documento

### Compilación Local (TeX Live / MiKTeX)
Para procesar correctamente los índices, las referencias cruzadas y la bibliografía (biber), debes ejecutar la siguiente secuencia en tu terminal o configurarla en tu editor (VS Code con LaTeX Workshop):

1. **`pdflatex main`** (Primera pasada del documento)
2. **`biber main`** (Procesamiento de la bibliografía)
3. **`pdflatex main`** (Integración de referencias)
4. **`pdflatex main`** (Resolución de índices y números de página)

### Compilación en Overleaf
1. Sube la carpeta del proyecto a un nuevo proyecto vacío en Overleaf.
2. Abre la configuración del proyecto en Overleaf (icono de engranaje / Menu).
3. Asegúrate de configurar:
   * **Compiler:** `pdfLaTeX`
   * **TeX Live Version:** `2023 (o posterior)`
   * **Main document:** `main.tex`
4. Haz clic en **Recompile**.

---

## 🧹 Limpieza del Proyecto
Al trabajar localmente, LaTeX genera múltiples archivos auxiliares (`.aux`, `.log`, `.toc`, etc.). Estos archivos están incluidos en `.gitignore` para no ensuciar el repositorio de Git. 
Puedes borrarlos de tu explorador de archivos local en cualquier momento si quieres liberar espacio, ya que se vuelven a generar de forma automática en cada compilación.
