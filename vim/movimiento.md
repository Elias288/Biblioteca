# Movimiento del cursor en VIM

```sh
          ↑
  ┌───┐ ┌───┐ ┌───┐ ┌───┐
← │ h │ │ j │ │ k │ │ l │ →
  └───┘ └───┘ └───┘ └───┘
                ↓
```

---

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

