---
title: Intro
has_children: false
nav_order: 1
---

VTEX IO es una plataforma de desarrollo serverless en la nube. Fue diseñada para crear aplicaciones web escalables y listas para su ejecución, sin tener que preocuparse por la complejidad de la infraestructura  

[Documentación](https://developers.vtex.com/vtex-developer-docs/docs/getting-started){: .md-button .md-button--primary }

[Release notes](https://github.com/vtex-apps/release-notes/releases){: .md-button }
## Playground

Accede al sitio de pruebas privado de Summa  
<small>(Siempre utilizar la opción de login ‘Google’ con tu correo empresarial)</small>

[Ambiente](http://summasolutions.myvtex.com)

---

## A tener en cuenta

Hasta el dia de la creación de esta documentación, VTEX IO está en etapa de desarrollo, por lo que han separado su ecosistema en 2

- **Store Framework (OPEN BETA)**
  Framework de implementación con componentes prediseñados para lanzar tiendas rápidamente; Store Framework está construido sobre IO.  
  Cualquier ambiente de VTEX puede pedir su instalación; prácticamente todos los ambientes ya son _Store-ready_  
  <small>Se construye utilizando SOLAMENTE apps nativas plug&play. </small>

- **IO (CLOSED BETA)**
  Plataforma de desarrollo ‘low-code’ basada en React  
  Podemos crear todas las apps con el builder de _React_ que querramos. Si se requiere algun builder adicional (Node, Pages, etc) se debe pedir permiso con un [formulario](https://developers.vtex.com/vtex-developer-docs/docs/vtex-io-documentation-filling-the-application-form-for-development)

---

## ¿Que son las apps?

Son prácticamente todo el ecosistema de VTEX IO  
Desde el admin, al store-front, al backend, todo se conforma por componentes denominados apps

VTEX aloja en github su catalogo completo de apps nativas plug & play

[Repositorio de aplicaciones nativas](https://github.com/vtex-apps)

---

## Workspaces

Son espacios de trabajo aislados unos de otros; funcionan como los branches de git, donde se puede desarrollar en un ambiente separado de los demas  
Hay tres tipos de espacios de trabajo

### Development

Entorno donde se puede vincular, desarrollar, instalar y publicar aplicaciones libremente

### Production

Entorno que maneja el tráfico de nivel de producción, se puede utilizar para pruebas A / B y se puede promover para convertirse en el espacio de trabajo principal

### Master

Espacio de trabajo de producción **único** en el que el contenido refleja lo que se sirve al usuario final de la tienda
