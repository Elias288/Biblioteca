# Comandos vim vscode

> v0.0.4

## Indice

- [Comandos vim vscode](#comandos-vim-vscode)
  - [Indice](#indice)
  - [Vim](#vim)
  - [Archivo](#archivo)
  - [Movimiento del cursor](#movimiento-del-cursor)
    - [Vertical](#vertical)
    - [Horizontal](#horizontal)
  - [Inserción](#inserción)
    - [Comandos en modo inserción](#comandos-en-modo-inserción)
  - [Edición](#edición)
    - [Reemplazar](#reemplazar)
    - [Copiar](#copiar)
    - [Cortar](#cortar)
    - [Cortar y reemplazar](#cortar-y-reemplazar)
    - [Pegar](#pegar)
  - [Buscar y Reemplazar](#buscar-y-reemplazar)
  - [Buffer](#buffer)
    - [Navegación del buffer](#navegación-del-buffer)
    - [Manejo de ventanas](#manejo-de-ventanas)
    - [Pestañas](#pestañas)
  - [Selección](#selección)
    - [Comandos en modo selección](#comandos-en-modo-selección)
  - [Navegar (solo vscode)](#navegar-solo-vscode)
  - [Plegado](#plegado)

## Vim

| Comando                                | Descripción                                            |
| -------------------------------------- | ------------------------------------------------------ |
| `:ter[minal]`                          | Abre una terminal.                                     |
| `:set nu[mber]`                        | Muestra en el editor el numero de cada linea.          |
| `:set nu!` o `:set nonumber`           | Oculta en el editor el numero de cada linea.           |
| `:set rnu` o `:set relativenumber`     | Muestra en el editor el numero relativo de cada linea. |
| `:set nornu` o `:set norelativenumber` | Oculta en el editor el numero relativo de cada linea.  |

## Archivo

| Comando | Descripción                                       |
| ------- | ------------------------------------------------- |
| `:w`    | Guardar archivo.                                  |
| `:q`    | Cerrar archivo.                                   |
| `:q!`   | Cerrar archivo sin guardar.                       |
| `:wq`   | Guardar y cerrar archivo siempre.                 |
| `:wqa`  | Guardar y cerrar todas las pestañas.              |
| `:x`    | Guarda solo si hubo cambios y cierra.             |
| `:e!`   | Recarga el archivo descartando todos los cambios. |

[volver](#comandos-vim-vscode)

## Movimiento del cursor

```sh
          ↑
  ┌───┐ ┌───┐ ┌───┐ ┌───┐
← │ h │ │ j │ │ k │ │ l │ →
  └───┘ └───┘ └───┘ └───┘
                ↓
```

### Vertical

| Comando     | Descripción                                       |
| ----------- | ------------------------------------------------- |
| `G`         | Mover el cursor a la primera linea del documento. |
| `gg`        | Mover el cursor a la última linea del documento.  |
| `<numero>G` | Mover el cursor a la linea `<numero>`.            |
| `{`         | Mover el cursor al anterior párrafo.              |
| `}`         | Mover el cursor al siguiente párrafo.             |
| `H`         | Mover el cursor al principio de la pantalla.      |
| `M`         | Mover el cursor al medio de la pantalla.          |
| `L`         | Mover el cursor al final de la pantalla.          |
| `Ctrl + b`  | Mover el cursor una pantalla completa anterior.   |
| `Ctrl + f`  | Mover el cursor una pantalla completa siguiente.  |
| `Ctrl + d`  | Mover el cursor 1/2 pantalla anterior.            |
| `Ctrl + u`  | Mover el cursor 1/2 pantalla siguiente.           |

[volver](#comandos-vim-vscode)

### Horizontal

- `0`: Mover el cursor hasta el inicio de la linea.

```sh
  ┌──────────────────────────
  Dolor consequat qui aliqua█
```

- `$`: Mover el cursor hasta el final del texto.

```sh
  ────────────────────────────────────────────────────────────
  █Dolor consequat qui aliqua. Voluptate elit quis non laborum
  ───────────────────────────┐
  laboris id et deserunt ad id.
```

- `g_`: Mover el cursor al último carácter al final de la linea.

```sh
  ──────────────────────────┐
  █Dolor-consequat-qui aliqua. 
  Voluptate elit quis non laborum laboris id et deserunt ad id.
```

- `w`: Mover el cursor al principio de la siguiente palabra.

```sh
  ───────┐
  █Dolor consequat qui aliqua
```

- `e`: Mover el cursor al final de la siguiente palabra.

```sh
  ─────┐
  █Dolor consequat qui aliqua
```

- `b`: Mover el cursor al principio de la anterior palabra.

```sh
  ┌──────
  Dolor █consequat qui aliqua
```

- `ge`: Mover el cursor al final de la anterior palabra.

```sh
      ┌──────────
  Dolor consequat█ qui aliqua
```

- `W`: Mover el cursor al principio de la siguiente palabra (hasta el siguiente espacio).

```sh
  ─────────────────────┐
  █Dolor-consequat-qui aliqua
```

- `E`: Mover el cursor al final de la siguiente palabra sin contemplar símbolos (hasta el siguiente espacio)

```sh
  ───────────────────┐
  █Dolor-consequat-qui aliqua
```

- `B`: Mover el cursor al principio de la anterior palabra (hasta el anterior espacio).

```sh
  ┌───────────────────
  Dolor-consequat-qui █aliqua
```

| Comando    | Descripción                                                                      |
| ---------- | -------------------------------------------------------------------------------- |
| `f<letra>` | Mover el cursor sobre la siguiente aparición de la `<letra>` (key sensitive).    |
| `t<letra>` | Mover el cursor antes de la siguiente aparición de la `<letra>` (key sensitive). |
| `F<letra>` | Mover el cursor sobre la anterior aparición de la `<letra>` (key sensitive).     |
| `T<letra>` | Mover el cursor antes de la anterior aparición de la `<letra>` (key sensitive).  |
| `^`        | Mover el cursor al primer carácter después de un salto de linea.                 |
| `zz`       | Centra la pantalla al cursor.                                                    |

[volver](#comandos-vim-vscode)

## Inserción

| Comando | Descripción                                     |
| ------- | ----------------------------------------------- |
| `i`     | Modo inserción antes del cursor.                |
| `a`     | Modo inserción después del cursor.              |
| `o`     | Modo inserción en la siguiente linea.           |
| `O`     | Modo inserción en la anterior linea.            |
| `I`     | Modo inserción al principio de la linea.        |
| `A`     | Modo inserción al principio de la linea.        |
| `ea`    | Modo inserción después de la siguiente palabra. |

[volver](#comandos-vim-vscode)

### Comandos en modo inserción

| Comando    | Descripción                                                 |
| ---------- | ----------------------------------------------------------- |
| `Ctrl + h` | Borrar carácter antes del cursor (en modo inserción).       |
| `Ctrl + w` | Borrar palabra después del cursor (en modo inserción).      |
| `Ctrl + t` | Identar linea (en modo inserción).                          |
| `Ctrl + d` | Des-Identar linea (en modo inserción).                      |
| `Ctrl + n` | Auto-completar con la siguiente opción (en modo inserción). |
| `Ctrl + p` | Auto-completar con la anterior opción (en modo inserción).  |

[volver](#comandos-vim-vscode)

## Edición

| Comando    | Descripción                             |
| ---------- | --------------------------------------- |
| `u`        | Deshacer.                               |
| `U`        | Rehacer ultima acción.                  |
| `Ctrl + r` | Rehacer.                                |
| `g~`       | Convierte todo un párrafo a mayúsculas. |
| `gu`       | Convierte toda una linea a minúsculas.  |
| `gU`       | Convierte toda una linea a mayúsculas.  |
| `.`        | Repetir último comando.                 |

[volver](#comandos-vim-vscode)

### Reemplazar

| Comando | Descripción                                             |
| ------- | ------------------------------------------------------- |
| `r`     | Reemplazar un solo carácter.                            |
| `R`     | Reemplazar más de un solo carácter.                     |
| `s`     | Eliminar un solo carácter y mantener el modo inserción. |
| `S`     | Eliminar toda una linea y mantener el modo inserción.   |

[volver](#comandos-vim-vscode)

### Copiar

| Comando                     | Descripción                           |
| --------------------------- | ------------------------------------- |
| `yy`                        | Copiar toda una linea.                |
| `y<número>y` o `<número>yy` | Copiar `<número>` cantidad de lineas. |
| `yw`                        | Copiar palabra.                       |
| `y0`                        | Copiar hasta el inicio de la linea.   |
| `y$` o `Y`                  | Copiar hasta el final de la linea.    |

[volver](#comandos-vim-vscode)

### Cortar

| Comando                     | Descripción                           |
| --------------------------- | ------------------------------------- |
| `dd`                        | Cortar toda una linea.                |
| `d<numero>d` o `<número>dd` | Cortar `<numero>` cantidad de lineas. |
| `dw`                        | Cortar una palabra.                   |
| `d0`                        | Cortar hasta el inicio de la linea.   |
| `d$` o `D`                  | Cortar hasta el final de la linea.    |
| `x`                         | Cortar carácter después del cursor.   |
| `X`                         | Cortar carácter antes del cursor.     |

[volver](#comandos-vim-vscode)

### Cortar y reemplazar

| Comando     | Descripción                                      |
| ----------- | ------------------------------------------------ |
| `cw` - `ce` | Cortar y reemplazar palabra.                     |
| `cc`        | Cortar y reemplazar toda una linea.              |
| `c0`        | Cortar y reemplazar hasta el inicio de la linea. |
| `c$` o `C`  | Cortar y reemplazar hasta el final de la linea.  |

[volver](#comandos-vim-vscode)

### Pegar

| Comando | Descripción               |
| ------- | ------------------------- |
| `p`     | Pegar después del cursor. |
| `P`     | Pegar antes del cursor.   |

[volver](#comandos-vim-vscode)

## Buscar y Reemplazar

| Comando                        | Descripción                                                                                  |
| ------------------------------ | -------------------------------------------------------------------------------------------- |
| `?<patrón>`                    | Busca patrón en todo el archivo para el inicio.                                              |
| `/<patrón>`                    | Busca patrón en todo el archivo para el final.                                               |
| `n`                            | Siguiente aparición del patrón.                                                              |
| `N`                            | Anterior aparición del patrón.                                                               |
| `:s/<patrón>/<nuevoPatrón>`    | Busca y reemplaza la primera aparición del patrón en una linea.                              |
| `:s/<patrón>/<nuevoPatrón>/gc` | Busca y reemplaza todas las apariciones del patrón (preguntando por cada una) en una linea.  |
| `:%s/<patrón>/<nuevoPatrón>`   | Busca y reemplaza todas las apariciones del patrón en el archivo.                            |
| `:%s/<patrón>/<nuevoPatrón>/c` | Busca y reemplaza todas las apariciones del patrón (preguntando por cada una) en el archivo. |

[volver](#comandos-vim-vscode)

## Buffer

| Comando              | Descripción                                                       |
| -------------------- | ----------------------------------------------------------------- |
| `:e[dit] <file>`     | Abre o crea un nuevo archivo en el buffer.                        |
| `:bd[elete]`         | Cierra el archivo del buffer.                                     |
| `:ls` o `:buffers`   | Lista todos los archivos en el buffer.                            |
| `:sp[lit] <file>`    | Abre un archivo en el buffer y divide al ventana horizontalmente. |
| `:vs[plit] <file>`   | Abre un archivo en el buffer y divide al ventana verticalmente.   |
| `:vert[ical] ba[ll]` | Muestra los archivos en buffer dividiendo la ventana.             |

### Navegación del buffer

| Comando            | Descripción                               |
| ------------------ | ----------------------------------------- |
| `:bn[ext]`         | Navega al siguiente archivo en el buffer. |
| `:bp[revious]`     | Navega al anterior archivo en el buffer.  |
| `:b[uffer]#`       | Navega al archivo con #.                  |
| `:b[uffer] <file>` | Navega al archivo por nombre.             |

### Manejo de ventanas

| Comando           | Descripción                                                       |
| ----------------- | ----------------------------------------------------------------- |
| `Ctrl + w(hjkl)`  | Mover el cursor por las ventanas.                                 |
| `Ctrl + w(HJKL)`  | Cambia la posición de la ventana en la dirección ingresada.       |
| `Ctrl + ws`       | Dividir la ventana actual horizontalmente.                        |
| `Ctrl + wv`       | Dividir la ventana actual verticalmente.                          |
| `Ctrl + ww`       | Cambiar de ventana.                                               |
| `Ctrl + wq`       | Cerrar ventana.                                                   |
| `Ctrl + wx`       | Intercambiar la ventana actual con la siguiente.                  |
| `Ctrl + w=`       | Iguala tamaños de ventanas en altura y anchura.                   |
| `Ctrl + w[<num>]>`| Aumenta el tamaño de la ventana <num> veces hacia la derecha.     |
| `Ctrl + w[<num>]<`| Aumenta el tamaño de la ventana <num> veces hacia la izquierda.   |
| `Ctrl + w[<num>]+`| Aumenta el tamaño de la ventana <num> veces hacia arriba.         |
| `Ctrl + w[<num>]-`| Aumenta el tamaño de la ventana <num> veces hacia abajo.          |

### Pestañas

| Comando                   | Descripción                                       |
| ------------------------- | ------------------------------------------------- |
| `:tabnew <file>`          | Abre o crea un nuevo archivo en una nuea pestaña. |
| `:tab ba[ll]`             | Muestra los archivos en buffer como pestañas.     |
| `gt` o `:tabn[ext]`       | Navegar a la pestaña siguiente.                   |
| `gT` o `:tabp[revious]`   | Navegar a la pestaña anterior.                    |
| `#gt`                     | Navega a la pestaña #                             |
| `Ctrl + wT`               | Mover la ventana actual a su propia ventana.      |
| `:tabc[lose]`             | Cerrar todas las pestañas                         |
| `:tabo[nly]`              | Cerrar todas las pestañas salvo la actual         |
| `:tabdo <comando>`        | Ejecuta el comando en todas las pestañas          |

[volver](#comandos-vim-vscode)

## Selección

| Comando | Descripción                                        |
| ------- | -------------------------------------------------- |
| `v`     | Modo seleccionar.                                  |
| `V`     | Modo seleccionar linea.                            |
| `o`     | Mover cursor de selección al principio y al final. |

### Comandos en modo selección

| Comando     | Descripción                                      |
| ----------- | ------------------------------------------------ |
| `ab` o `a(` | Selecciona el siguiente par de ().               |
| `aB` o `a{` | Selecciona el siguiente par de {}.               |
| `ib` o `i(` | Selecciona el contenido del siguiente par de (). |
| `iB` o `i{` | Selecciona el contenido del siguiente par de {}. |

[volver](#comandos-vim-vscode)

## Navegar (solo vscode)

| Comando | Descripción                   |
| ------- | ----------------------------- |
| `gd`    | Navegar a definición.         |
| `gt`    | Navegar a definición de tipo. |
| `gq`    | Mostrar sugerencias.          |
| `gh`    | Ver mensaje.                  |
| `gi`    | Navegar a implementación.     |
| `gr`    | Navegar a referencias.        |

[volver](#comandos-vim-vscode)

## Plegado

| Comando | Descripción                         |
| ------- | ----------------------------------- |
| `za`    | Alternar pliegue/despliegue bloque. |
| `zc`    | Plegar bloque.                      |
| `zo`    | Desplegar bloque.                   |

[volver](#comandos-vim-vscode)
