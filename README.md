```markdown
# 🧩 SudokuSensei

> _El sensei que resuelve tus sudokus con inteligencia humana y heurísticas avanzadas_

![Python Version](https://img.shields.io/badge/python-3.6+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen.svg)

**SudokuSensei** es un solucionador de Sudoku en Python que combina **técnicas humanas** (pares desnudos, pares ocultos, X-Wing, etc.) con **heurísticas de IA** (MRV + Forward Checking) para ofrecer una experiencia educativa y eficiente. Además, cuenta con una **interfaz gráfica (Tkinter)** y una **versión web con Flask**, permitiendo arrastrar archivos, ver el progreso paso a paso, exportar a PDF y mucho más.

---

## 📸 Capturas de pantalla

> _(Pronto añadiremos imágenes, pero imagina una GUI bonita con cuadrícula, botones y un registro de técnicas aplicadas)_

---

## ✨ Características principales

- ✅ **Resolución por backtracking** (clásico) y **backtracking con MRV + Forward Checking** (más rápido).
- 🧠 **Técnicas humanas**:
  - Pares desnudos (Naked Pairs) en filas, columnas y cajas.
  - Pares ocultos (Hidden Pairs) – ¡nuevo!
  - X-Wing (versión básica) – ¡nuevo!
- 📜 **Registro de técnicas**: cada paso queda guardado y se muestra en la GUI o en consola.
- 🖥️ **Interfaz gráfica con Tkinter**:
  - Edición directa de celdas.
  - Botones para cargar archivo, resolver, paso a paso, limpiar, exportar PDF y ayuda.
  - Widget de texto con el log de técnicas aplicadas.
- 📂 **Arrastrar y soltar archivos** (en la versión web y próximamente en la GUI).
- 🌐 **Versión web con Flask**: interfaz moderna, subida de archivos por drag & drop, visualización del log.
- 📄 **Exportación a PDF** de la solución (con `reportlab`).
- 🎨 **Colores en consola** (si tienes `colorama`).

---

## 📦 Instalación

### Requisitos previos
- Python 3.6 o superior.
- Pip (gestor de paquetes).

### Dependencias opcionales
| Paquete     | Uso                          | Instalación                     |
|-------------|------------------------------|---------------------------------|
| `colorama`  | Colores en consola           | `pip install colorama`          |
| `reportlab` | Exportar a PDF               | `pip install reportlab`         |
| `flask`     | Versión web                  | `pip install flask`             |
| `tkinter`   | GUI (suele venir con Python) | En Ubuntu: `sudo apt install python3-tk` |

### Clonar el repositorio
```bash
git clone https://github.com/tuusuario/sudoku-sensei.git
cd sudoku-sensei
```

### Instalar dependencias (todas)
```bash
pip install -r requirements.txt
```

> **Nota**: Si no quieres todas, instala solo las que necesites.

---

## 🚀 Uso

### Modo consola (CLI)

```bash
python sudoku_sensei.py -f puzzle.txt --steps --delay 0.2
```

Opciones disponibles:
- `-f`, `--file` : archivo con el tablero.
- `-i`, `--interactive` : entrada manual (9 líneas).
- `-s`, `--steps` : mostrar cada paso.
- `-d`, `--delay` : tiempo entre pasos.
- `-c`, `--count` : contar soluciones.
- `-g`, `--generate` : generar un tablero resuelto.
- `--cli` : forzar modo consola.
- `--gui` : abrir la interfaz gráfica.

Ejemplo completo:
```bash
python sudoku_sensei.py -f sudoku.txt --steps --delay 0.5 --count
```

### Interfaz gráfica (Tkinter)

```bash
python sudoku_sensei.py --gui
```

O simplemente ejecuta sin argumentos (si Tkinter está disponible se abrirá la GUI).

Desde la GUI puedes:
- Editar celdas directamente.
- Cargar archivo `.txt`.
- Resolver con técnicas humanas o con backtracking.
- Ver el log de técnicas en un panel lateral.
- Exportar la solución a PDF.

### Versión web (Flask)

```bash
python web_app.py
```

Luego abre tu navegador en `http://localhost:5000`. Allí podrás:
- Arrastrar y soltar un archivo de texto.
- Ver el tablero y el log de técnicas.
- Resolver y descargar el PDF.

---

## 📂 Formato del archivo de entrada

El archivo debe tener **9 líneas**, cada una con **9 números** separados por espacio. Usa `0` para las celdas vacías.

Ejemplo (`puzzle.txt`):
```
5 3 0 0 7 0 0 0 0
6 0 0 1 9 5 0 0 0
0 9 8 0 0 0 0 6 0
8 0 0 0 6 0 0 0 3
4 0 0 8 0 3 0 0 1
7 0 0 0 2 0 0 0 6
0 6 0 0 0 0 2 8 0
0 0 0 4 1 9 0 0 5
0 0 0 0 8 0 0 7 9
```

---

## 🧠 Técnicas humanas implementadas

| Técnica               | Descripción                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **Naked Pairs**       | Dos celdas en la misma unidad con exactamente los mismos dos candidatos. Elimina esos valores del resto de la unidad. |
| **Hidden Pairs**      | Dos números que solo aparecen en dos celdas de una unidad. Elimina otros candidatos de esas celdas. |
| **X-Wing** (básico)   | Un patrón en el que un número aparece en exactamente dos filas y dos columnas, formando un rectángulo. Elimina el número de otras celdas en esas filas/columnas. |

Estas técnicas se aplican de forma iterativa antes de recurrir al backtracking, reduciendo drásticamente el espacio de búsqueda.

---

## 🔧 Futuras mejoras (contribuciones bienvenidas)

- [ ] Añadir más técnicas humanas: *Swordfish*, *XY-Wing*, *Coloring*, etc.
- [ ] Mejorar el widget de log en la GUI (con scroll y formato).
- [ ] Soporte para arrastrar y soltar en la GUI nativa (Tkinter no lo soporta directamente, pero se puede emular).
- [ ] Modo "entrenador" que explique cada técnica paso a paso.
- [ ] Versión móvil (PWA) con la API Flask.
- [ ] Integración con bases de datos para guardar partidas.

Si quieres colaborar, ¡abre un issue o un pull request! Toda ayuda es bienvenida.

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Si lo usas, solo te pedimos que menciones al autor (y que compartas tus mejoras 😉).

---

## 🙏 Agradecimientos

- A los creadores de `colorama`, `reportlab` y `flask` por sus increíbles librerías.
- A la comunidad de Python por su constante apoyo.
- A ti, por leer hasta aquí. ¡Ahora ve a resolver sudokus como un sensei!

---

## 📬 Contacto

Si tienes dudas, sugerencias o simplemente quieres charlar sobre Sudoku, escríbeme a:  
**visintinitech@gmail.com** 

---

**¡Que la fuerza (y el backtracking) te acompañe!** 🧘‍♂️
```

---

