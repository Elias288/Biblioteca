# Configuración de Servidor

Configuraciones de un servidor debian basado en el video [Asegurar servidor linux](https://www.youtube.com/watch?v=_Hcm9ksOkqU&list=WL&index=2), donde se configura usuario con permisos root, conexión ssh por clave, actualizaciones automaticas y vaneo de fuerza bruta.

**Indice**

- [Instalar programas básicos](#instalar-programas-básicos)
- [Configurar usuario](#configurar-usuario)
- [SSH](#ssh)
- [Evitar suspención de laptop](#evitar-suspención-de-laptop)
- [Actualizaciones automáticas](#actualizaciónes-automáticas)
- [Protección de fuerza bruta](#protección-de-fuerza-bruta)
- [Firewall UFW](#firewall-ufw)
- [Docker](#docker)

## Instalar programas básicos

Instalación de programas básicos

Ingresar como super usuario:

```sh
su -
```

Actualizar sistema

```sh
apt upgrade
```

Instalar `sudo`, `vim` y `tmux` 

```sh
apt install sudo tmux vim curl ufw
```

## Configurar usuario

Crear usuario y asignarle permisos de superusuario.

1. Crear usuario:

```sh
adduser <username>
```

3. Agregarlo al grupo sudo:

```sh
usermod -aG sudo <username>
```

## SSH

Configurar SSH. Crear clave, enviarla al servidor y configurar para no aceptar conexion por contraseña.

En la pc principal configurar clave:

```sh
ssh-keygen -t ed25519
```

Enviarla al servidor

```sh
ssh-copy-id eleli@192.168.1.30
```

Configurar para no aceptar conexiones de ssh. Duplicar archivo `/etc/ssh/sshd_config`:

```sh
sudo cp /etc/ssh/sshd_cofig /etc/ssh/sshd_config_back
```

Editar archivo `sshd_config`

```
...
PasswordAuthentication no
...
PermitRootLogin no
```

Reiniciar servicio sshd

```sh
sudo service sshd restart
```

## Evitar suspención de laptop

En caso que el servidor sea una laptop, para evitar que esta se suspenda al cerrar la pantalla hay que:

Modificar el archivo `/etc/systemd/logind.conf` como super usuario y modificar las siguientes lineas:

```
...
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
...
LidSwitchIgnoreInhibited=no
...
```

Aplicar cambios

```sh
sudo systemctl restart systemd-logind.service
```

## Actualizaciónes automáticas

Basado en la [wiki de debian](https://wiki.debian.org/UnattendedUpgrades) los pasos para instalar y configurar actualizaciones automáticas.

```sh
sudo apt install unattended-upgrades
```

En el archivo `/etc/apt/apt.conf.d/50unattended-upgrades` se encuentran los paquetes que se actualizarán. Por defecto se actualizan los paquetes de seguridad.

Se debe crear el archivo `/etc/apt/apt.conf.d/20auto-upgrades` donde se configurará cada cuanto tiempo se deben realizar las actualizaciones.

```sh
sudo touch /etc/apt/apt.conf.d/20auto-upgrades
sudo vim /etc/apt/apt.conf.d/20auto-upgrades
```

```sh
# 20auto-upgrades
APT::Periodic::Update-Package-Lists "1"; # cada cuantos días se actualizará la lista de paquetes
APT::Periodic::Unattended-Upgrade "1";   # activar las actualizaciones automaticas
APT::Periodic::AutocleanInteral "7"      # limpia los paquetes obsoletos
```

Ejecutar testeo

```sh
sudo unattended-upgrade --dry-run --debug
```

## Protección de fuerza bruta

Para evitar intentos de ingreso por fuerza bruta se configurará `fail2ban` que baneará la ip si detecta repetidos intentos de conexión.

Instalar `fail2ban`

```sh
sudo apt install fail2ban
```

Configurar archivo `jail.local` donde estará nuestra configuración

```sh
sudo touch /etc/fail2ban/jail.local
sudo vim /etc/fail2ban/jail.local
```

```sh
# jail.local
[DEFAULT]
...
[sshd]
backend=systemd
enable=true
...
```

Habilitar e iniciar `fail2ban`

```sh
sudo systemctl enable fail2ban.service
sudo systemctl start fail2ban
```

Ver estado del servicio

```sh
sudo systemctl status fail2ban.service
sudo fail2ban.client status
```

## Firewall UFW

Ya teniendo instalado `ufw` se realizarán las siguientes [configuraciones](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-10).

Por defecto denegará todas las conexiones entrantes y permitirá todas las salientes:

```sh
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Permitiremos las conexiones entrantes para `ssh`, `http` y `https`:

```sh
sudo ufw allow [ssh/<port>]
sudo ufw allow http
sudo ufw allow https
```

Habilitar firewall y ver estado

```sh
sudo ufw enable
sudo ufw status verbose
```

> Solo se necesitan abrir los puertos de ssh, 80 y 443.

## Docker

Para [instalar docker](https://docs.docker.com/engine/install/debian/) seguiremos los siguientes pasos:

```sh
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

