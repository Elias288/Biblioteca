# Barrier

Barrier es una herramienta multipĺataforma para conmpartir teclado y mouse mediante ssh. Esto permite compartir mouse y teclado entre windows y linux.

La instalación es bastante sencilla desde su [github](https://github.com/debauchee/barrier).

## Conexión

Desde la PC donde está conectados el mouse y el teclado se debe configurar como servidor, lo que nos permitirá configurar la posición y el equipo cliente al que le queremos comparir los inputs (tener en cuenta que el nombre del cliente debe ser el mismo).

Desde el lado del cliente hay que configurarlo como tal e ingresar la ip del servidor.

Una vez configurados iniciaremos el servidor (F2 para ver los logs si hay errores) y el cliente.

El servidor no se detendrá si lo cerramos, para finalizar la conexión hay que precionar el botón detener.

## Certificado SSL

Link del [issue](https://github.com/debauchee/barrier/issues/231#issuecomment-659377040)

Una vez instalado y configurado es posible que no se genere el cerificado ssl necesario para encriptar la conexión por lo que hay que realizar un paso más:

Path de **Windows**:

```sh
C:\Users\<user>\AppData\Local\Barrier\SSL
```

Path de **Linux**:

```sh
/Home/<user>/.local/share/barrier/SSL
```

Generar certificado SSL:

```sh
openssl req -x509 -nodes -days 365 -subj /CN=Barrier -newkey rsa:4096 -keyout Barrier.pem -out Barrier.pem
```

## Bug Windows server

Link del [issue](https://github.com/debauchee/barrier/issues/500#issuecomment-559142339)

Es posible que si el servidor se encuentra del lado de windows ocurra un bug en el cliente que proboca que el mouse no se mueva. Esto se soluciona entrando al path de instalación de `Barrier` en windows y modificar la configuración de compatibilidad del archivo `barriers.exe` que se encuentra en:

```sh
C:\Program Files\Barrier\barriers.exe
```

Entramos a:

click derecho --> propiedades --> Compatibilidad --> Cambiar configuración para todos los usuarios  --> Cambiar configuración elevada de PPP

y marcamos la ultima casilla `Invalidar el comportamiento de ajuste con valores altos de PPP`

