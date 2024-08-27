# Linux Alias

En linux se pueden configurar "alias", formas alternativas o abreviadas de ejecutar comandos en consola. Estos "alias" se pueden configurar de 2 formas:

## Comando Alias

Mediante el comando `alias` siguiendo el siguiente formato `alias <aliasName>="<command>"`

Ejemplo:

```sh
alias ll="ls -l"
```

## Archivo .bashrc

En este archivo se encuentran las configuraciones de la consola. Idea sacada desde este [video](https://www.youtube.com/watch?v=UmeediMPr6k&list=TLPQMjcwODIwMjSimdDT7-fdgg&index=2
).

Ejemplo de alias configurados:

```sh
export EDITOR=/usr/bin/vim

# Comon commands
alias \
	ls="ls -hN --color=auto --group-directories-first" \
	ll="ls -l --color=auto --group-directories-first" \
	lsa="ls -lahN --color=auto --group-directories-first" \
	mv="mv -iv" \
	rm="rm -iv" \
	cp="cp -iv" \
	mkdir="mkdir -pv" \
	e="$EDITOR" \
	v="$EDITOR" \
	cl="clear"

# Accesos rapidos
alias \
	h="cd" \

# GIT
alias \
	g="git"
```

