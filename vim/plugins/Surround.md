# [Surround](https://vimawesome.com/plugin/surround-vim)

Plugin para facilitar el modificar o agregar elementos alrededor de una palabra o texto.

## Comandos

| Comandos                 | Descripción                                                           |
| ---                      | ---                                                                   |
| `ysiw<element>`          | Agrega `<element>` alrededor de una palabra                           |
| `yss<element>`           | Agrega `<element>` alrededor de una linea                             |
| `cs<element1><element2>` | Intercambia `<element1>` por el `<element2>`                          |
| `cst<element>`           | Si el element es de más de un caracter lo intercambia por `<element>` |
| `ds<element>`            | Elimina el `<element>`                                                |


## Comentarios

- Si se usa una llave inicial (`{`, `[` o `(`) se rodeará agregando espacios. `{ text }`.
- Si se usa una llave final (`}`, `]` o `)`) se rodeará sin espacios. `{text}`.
- `)` puede ser escrito como `b`.

