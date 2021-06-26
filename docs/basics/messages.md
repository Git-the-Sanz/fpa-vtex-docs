---
layout: default
title: Messages
parent: Basics
nav_order: 5
---

Por defecto, las aplicaciones nativas vienen con textos en diferentes idiomas, incluido el Español; a veces es necesario cambiarlos de acuerdo al requerimiento del cliente, para eso podemos hacer uso de la app encargada de mutar estos `messages`  

[Instrucciones](https://developers.vtex.com/vtex-developer-docs/docs/storefront-content-internationalization){: .md-button .md-button--primary }

!!! warning
    Esto requiere tener instalada [admin-graphql-ide](https://github.com/vtex-apps/admin-graphql-ide)

Por ejemplo, de acuerdo a las instrucciones previamente mencionadas, en la carpeta de `messages` del [minicart](https://github.com/vtex-apps/minicart/blob/master/messages/es.json) podemos ver que el texto nativo de `"store/minicart.go-to-checkout"` es **"Cerrar pedido"**  

De acuerdo al step by step, si ingresamos:

```json
{
  "saveArgs": {
    "to": "es-AR",
    "messages": [
      {
        "srcLang": "en-DV",
        "srcMessage": "store/minicart.go-to-checkout",
        "context": "vtex.minicart@2.x",
        "targetMessage": "Finalizar compra"
      }
    ]
  }
}
```

Vamos a poder ver que el boton para ir al checkout cambio a **"Finalizar compra"**

!!! info
    Recorda que SIEMPRE el **srcLang** es "en-DV" y el **to** es "es-AR"

---

## ICU Formatted Messages

Algunas apps como [product price](https://vtex.io/docs/components/all/vtex.product-price@1.21.0/) contienen mensajes que pueden ser customizados desde el Site Editor, porque adicionalmente contienen variables para interpolar.

Por ejemplo:

```json
{
  "product-selling-price": {
    "props": {
      "message": "{sellingPriceWithUnitMultiplier}{hasMeasurementUnit,
      select, true { / {hasUnitMultiplier, select, true {{unitMultiplier}}
      false {}} {measurementUnit}} false {}}"
    }
  }
}
```

Una herramienta util para poder generar mensajes complejos es la [Online ICU Message Editor](https://format-message.github.io/icu-message-format-for-translators/editor.html)