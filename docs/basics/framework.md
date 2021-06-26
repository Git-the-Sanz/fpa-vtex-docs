---
layout: default
title: Store Framework
parent: Basics
nav_order: 1
---

Se encarga de definir la estructura básica de cualquier tienda en la plataforma.
Es la interfaz entre la tienda y el desarrollador mediante los denominados _Builders_

[Boilerplate](https://bitbucket.org/summasolutions/vtex-theme-boilerplate)  
<small>Este es nuestro jumpstart para crear tiendas</small>

---

## Builders

Un builder es básicamente una abstracción para configurar otros servicios en IO. Se encarga de interpretar el código de otras aplicaciones y transformarlo a un objetivo determinado, funcionando como un servicio API que procesa e interpreta un directorio en la app

Por ejemplo

- _Store Builder_ -> Encargado de interpretar los bloques
- _GraphQL Builder_ -> Encargado de interpretar las llamadas a la API
- _React Builder_ -> Encargado de interpretar apps customizadas
- _Styles Builder_ -> Encargado de interpretar la configuración de Tachyons
- _Y más_

---

## Custom theme example

A partir de este framework, vamos a poder crear nuestros propios ‘themes’  
VTEX nos demuestra la capacidad de esto con un ejemplo  
[Store theme](https://github.com/vtex-apps/store-theme)

---

## Dependencies

Este campo especifica en qué aplicaciones tu aplicacion de VTEX IO se basa para funcionar correctamente. Su semántica se asemeja a la propiedad de dependencias de `package.json` en aplicaciones Javascript.  

[Leer más](https://developers.vtex.com/vtex-developer-docs/docs/vtex-io-documentation-dependencies)

## Peer dependencies

A diferencia de las dependencias normales, las `peer dependencies` no se instalan automáticamente en una cuenta. Por lo tanto, son especialmente útiles para los casos en los que una aplicación se basa en otra aplicación de paga.

Otro caso de uso para el campo `peer dependencies` es cuando la aplicación se basa en otra que tiene diferentes versiones principales, lo que puede afectar las funcionalidades de otras aplicaciones según la versión instalada.  

[Leer más](https://developers.vtex.com/vtex-developer-docs/docs/vtex-io-documentation-peerdependencies)

---

## Plugins

Las aplicaciones también pueden insertar sus bloques en otros componentes específicos de la página. Los Plugins brindan una manera fácil de agregar funcionalidad específica en un modo plug and play a cualquier tienda, por ejemplo, el Botón Visa Checkout en el carrito de la compra.

---

## Routes

Para crear una ruta personalizada en VTEX IO, todo lo que se necesita es un template de página y una ruta.
Estas rutas deben declararse en el archivo `route.json` dentro de la carpeta `store` como en el siguiente ejemplo:

```json
{
    "store.custom#{templatename}": {
      "path": "/{URL}"
    }
}
```

[Leer más](https://developers.vtex.com/vtex-developer-docs/docs/routes)

---

## Interfaces

Las interfaces establecen una relación entre un bloque de store framework y un componente de React, lo que permite al Store Builder construir el front-end de la tienda. Se pueden encontrar dentro del archivo `interfaces.json` de una aplicación.  

Por ejemplo:

```json
// product-summary/store/interfaces.json
{
  "product-summary": {
    "component": "ProductSummary",
    "composition": "children",
    "content": {
      "$ref": "app:vtex.product-summary#/definitions/ProductSummary"
    }
  }
}
```

- `product-summary` es el nombre del bloque que va a ser usado en una tienda
- `component` es el componente de React al cual va a ser referenciado