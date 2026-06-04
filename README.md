# Guia del Proyecto y Estructura LaTeX

Este repositorio contiene la estructura modular y la configuracion de estilos para el informe tecnico:
"Diseño e implementacion de un sistema IoT para contenedores municipales utilizando tecnologia LoRa P2P en la manzana del Mercado San Camilo, Arequipa".

El documento ha sido diseñado siguiendo estandares formales de presentacion, utilizando una paleta de colores profesional y bloques de contenido estructurados.

---

## Estructura del Proyecto

El proyecto esta organizado de manera modular para facilitar la edicion colaborativa y el orden:

* main.tex: Archivo raiz principal que compila el documento.
* referencias.bib: Base de datos de bibliografia (formato BibLaTeX).
* .gitignore: Exclusiones de archivos auxiliares y compilados.
* README.md: Esta guia de trabajo.

* Carpetas del proyecto:
  * config/ (Configuraciones generales de LaTeX)
    * packages.tex: Carga de paquetes y librerias externas.
    * metadata.tex: Datos editables (Titulo, autor, docente, etc.).
    * styles.tex: Definicion de colores, margenes, tipografia y diseño.
    * macros.tex: Comandos personalizados y cajas (tcolorbox).
  * frontmatter/ (Paginas preliminares)
    * portada.tex: Estilo y distribucion de la caratula.
    * resumen.tex: Resumen y palabras clave.
  * sections/ (Capitulos del cuerpo del informe)
    * 01_introduccion.tex: Introduccion, justificacion y problematica.
    * 02_objetivos.tex: Objetivos generales y especificos.
    * 03_fundamento_teorico.tex: Marco teorico y conceptos clave.
    * 04_metodologia_ansys.tex: Configuracion de simulacion y metodologia.
    * 05_resultados.tex: Presentacion de resultados y simulaciones.
    * 06_discusion.tex: Discusion de los resultados obtenidos.
    * 07_conclusiones.tex: Conclusiones y trabajos futuros.
  * appendices/ (Anexos)
    * anexo_a.tex: Material complementario o codigos fuente.
  * figures/ (Recursos graficos e imagenes del informe)
    * logo.png: Logotipo institucional para la portada.
    * captura_placeholder.png: Imagen de muestra para metodologia.
    * resultado_placeholder.png: Imagen de muestra para resultados.

---

## Como Trabajar en el Proyecto

### 1. Configuracion de Datos Personales
Edita el archivo config/metadata.tex para personalizar la informacion general:
* Universidad, Facultad y Escuela.
* Titulo y subtitulo del informe.
* Nombre del docente y del curso.
* Nombre, codigo y grupo de los autores.

### 2. Escritura de Capitulos
Cada capitulo del informe esta separado en un archivo .tex dentro de la carpeta sections/. Para crear subsecciones estructuradas, utiliza:
```latex
\section{Nombre de la Seccion}
\subsection{Subseccion}
\subsubsection{Detalle especifico}
```

### 3. Insercion de Imagenes y Capturas
Se ha provisto una macro simplificada llamada \captura en config/macros.tex:
```latex
\captura[ancho]{ruta/de/la/imagen.png}{Titulo o descripcion de la figura}
```
* Ejemplo de uso: \captura[0.85]{figures/logo.png}{Logotipo oficial de la universidad.} (El ancho por defecto es 0.88 de la linea de texto).

### 4. Uso de Cajas Modernas y Semanticas
Para resaltar partes importantes del documento, utiliza las siguientes cajas de contenido personalizadas:
* Informacion General:
  ```latex
  \begin{infobox}
      Texto explicativo o informacion general complementaria.
  \end{infobox}
  ```
* Notas de Simulacion:
  ```latex
  \begin{warningbox}
      Detalles criticos sobre la simulacion en ANSYS o advertencias tecnicas.
  \end{warningbox}
  ```
* Resultados Clave:
  ```latex
  \begin{resultbox}
      Conclusiones y datos de salida de gran relevancia obtenidos de la simulacion.
  \end{resultbox}
  ```
* Tarjetas Conceptual/Teoricas:
  ```latex
  \begin{conceptcard}{Nombre del Concepto}
      Definicion concisa o formulas principales.
  \end{conceptcard}
  ```
* Bloques de Codigo Estilo Editor:
  ```latex
  \begin{codeeditor}{NombreArchivo.py}
  \begin{lstlisting}[language=Python]
  # Codigo aqui
  print("Hola Mundo")
  \end{lstlisting}
  \end{codeeditor}
  ```

### 5. Codigos QR Vectoriales Interactivos
Si quieres enlazar hojas de datos, repositorios de codigo o videos de simulacion, usa la macro \enlaceQR:
```latex
\enlaceQR[tamaño_qr]{url}{Titulo del Enlace}{Breve descripcion explicativa}
```
* Ejemplo: \enlaceQR{https://github.com}{Repositorio GitHub}{Acceso al codigo fuente del firmware del microcontrolador.}

### 6. Gestion de Referencias Bibliograficas
1. Añade tus entradas bibliograficas en formato BibTeX en el archivo referencias.bib.
2. Citalas en el texto usando el comando \cite{id_referencia}.
3. El documento las formateara automaticamente bajo la norma IEEE.

---

## Compilacion del Documento

### Compilacion Local (TeX Live / MiKTeX)
Para procesar correctamente los indices, las referencias cruzadas y la bibliografia (biber), debes ejecutar la siguiente secuencia:

1. pdflatex main (Primera pasada del documento)
2. biber main (Procesamiento de la bibliografia)
3. pdflatex main (Integracion de referencias)
4. pdflatex main (Resolucion de indices y numeros de pagina)

### Compilacion en Overleaf
1. Sube la carpeta del proyecto a un nuevo proyecto vacio en Overleaf.
2. Abre la configuracion del proyecto en Overleaf (Menu).
3. Asegurate de configurar:
   * Compiler: pdfLaTeX
   * TeX Live Version: 2023 (o posterior)
   * Main document: main.tex
4. Haz clic en Recompile.

---

## Limpieza del Proyecto
Al trabajar localmente, LaTeX genera multiples archivos auxiliares (.aux, .log, .toc, etc.). Estos archivos estan incluidos en .gitignore. Se pueden borrar del explorador de archivos local en cualquier momento si quieres liberar espacio, ya que se vuelven a generar de forma de automatica en cada compilacion.
