---
layout: default
title: Toolbelt
parent: Basics
nav_order: 3
---

# VTEX CLI

Cualquier desarrollo en VTEX IO comienza y termina con VTEX Toolbelt.  
Esta herramienta te permite iniciar sesión en una cuenta VTEX, vincular archivos locales a la plataforma, administrar los espacios de trabajo de una cuenta, además de realizar cualquier acción necesaria para su proceso de desarrollo

[Toolbelt](https://github.com/vtex/toolbelt)

---

## Flujo de uso

**`vtex login <account>`**  
<small>Linkea la instancia de la linea de comandos con el ambiente adecuado</small>

**`vtex whoami`**  
<small>Es buena practica utilizar este comando para saber en que cuenta y workspace estamos trabajando</small>

**`vtex use <name>`**  
<small>Nos ingresa a nuestro workspace elegido, si no existe, nos ofrece crearlo</small>

**`vtex list`**  
<small>Nos dice las apps instaladas y linkeadas</small>

**`vtex link`**  
<small>Para añadir la app la cual tenemos abierta en el mismo IDE</small>

**`vtex link [app]`**  
<small>
    Para añadir una app especifica.
    En el formato **[vendor].[app]@[version]**
</small>

--- 

Si vamos a empezar un desarrollo de React nuevo, siempre empecemos con  
**`vtex setup`**  
<small>Esto nos configura tsconfig y tslint</small>

!!! info
    Para la documentacion respecto a release/deploy referirse [aqui](/vtex-docs/development/release.html)