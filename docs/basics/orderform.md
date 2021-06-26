---
layout: default
title: Orderform
parent: Basics
nav_order: 4
---

# Orderform

Es el conjunto de datos principal para el _checkout_  
 
[App](https://github.com/vtex-apps/order-manager)  

Consta de varias secciones, cada una con información útil a la que se puede acceder y (posiblemente) modificar.  

Casi todas las operaciones en la API de Checkout devuelven Orderform (o parte de él).
 de estructura


```json
{
  "canEditData": true,
  "clientPreferencesData": …,
  "clientProfileData": …,
  "giftRegistryData": …,
  "items": …,
  "loggedIn": false,
  "marketingData": …,
  "messages": …,
  "orderFormId": "0123456789abcdeffedcba9876543210",
  "paymentData": …,
  "salesChannel": "1",
  "sellers": …,
  "shippingData": …,
  "storePreferencesData": …,
  "totalizers": …,
  "userProfileId": null,
  "userType": null,
  "value": 20980
}
```

## Convenciones

Las propiedades que representan valores monetarios tienen sus valores expresados ​​en centavos. Por ejemplo, 10990 significa R $ 109,90 en las tiendas brasileñas.

## Secciones

- [items](#items)
- [totalizers](#totalizers)
- [clientProfileData](#clientProfileData)
- [shippingData](#shippingData)
- [paymentData](#paymentData)
- [sellers](#sellers)
- [messages](#messages)
- [clientPreferencesData](#clientPreferencesData)
- [storePreferencesData](#storePreferencesData)

### items

Es un arreglo de objetos **item**. Cada **item** tiene información sobre un producto que está en el carrito del cliente, como nombre, precio y cantidad.


```json
[
  {
    "id": "2004075",
    "productId": "4741",
    "name": "Ração Club Performance Junior - Royal Canin Ração Club Performance Junior Royal Canin - Promocional 15 kg + 3 kg",
    "skuName": "Ração Club Performance Junior Royal Canin - Promocional 15 kg + 3 kg",
    "tax": 0,
    "price": 10490,
    "listPrice": 10490,
    "sellingPrice": 10490,
    "isGift": false,
    "additionalInfo": {
      "brandName": "Royal Canin Cães",
      "brandId": "37",
      "offeringInfo": null
    },
    "preSaleDate": null,
    "productCategoryIds": "/343/515/517/",
    "defaultPicker": null,
    "handlerSequence": 0,
    "handling": false,
    "quantity": 3,
    "seller": "1",
    "imageUrl": "/arquivos/ids/188329-71-71/racao-club-performance-junior.jpg",
    "detailUrl": "/racao-royal-canin-club-performance-junior/p",
    "components": [],
    "bundleItems": [],
    "offerings": [{
      "id": "1033",
      "name": "A Oferta Magnifica",
      "price": 100,
      "type": "idk"
    }],
    "priceTags": [],
    "availability": "available",
    "measurementUnit": "un",
    "unitMultiplier": 1
  }
]
```

### totalizers

Es un arreglo de objetos **totalizer**. Cada **totalizer** posee un `id` unico, un `name` descriptivo, y un `value`.


```json
[
  {
    "id": "Items"
    "name": "Total dos Itens"
    "value": 35620
  }, {
    "id": "Shipping"
    "name": "Total do Frete"
    "value": 399
  }
]
```

### clientProfileData

Es un objeto que representa los datos del cliente.  

Si el cliente aún no ha informado al correo electrónico, la mayoría de los datos pueden estar vacíos (`null`).  

Si el correo electrónico del cliente no ha sido confirmado, se censurarán varios datos personales.  


```json
{
  "attachmentId": "clientProfileData",
  "email": "gadr90@gmail.com",
  "firstName": "Gui******",
  "lastName": "Rod******",
  "document": "*1*3*8*7*0*",
  "documentType": "cpf",
  "phone": "******2121",
  "corporateName": null,
  "tradeName": null,
  "corporateDocument": null,
  "stateInscription": null,
  "corporatePhone": null,
  "isCorporate": false
}
```

### shippingData

Es un objeto que contiene:

- `address`: objeto que representa la direccion seleccionada  

- `availableAddresses`: array de objetos **address** disponibles  

- `logisticsInfo`: array de objetos, uno para cada artículo del carrito. Cada objeto contiene un array `slas`. Los elementos de este array son objetos **sla**, que contienen propiedades relacionadas con una opción de entrega.

Si el correo electrónico del cliente no ha sido confirmado, se censurarán varios datos personales.


```json
{
  "attachmentId": "shippingData",
  "address": {
    "addressType": "residential",
    "receiverName": "Gui***rme",
    "addressId": "-1368194386810",
    "postalCode": "******000",
    "city": "Rio ** *******",
    "state": "RJ",
    "country": "BRA",
    "street": "Rua *** *****nte",
    "number": "***",
    "neighborhood": "Bot*****",
    "complement": "*** ** *",
    "reference": null
  },
  "availableAddresses": [
    {
      "addressType": "residential",
      "receiverName": "Gui***rme",
      "addressId": "-1368194386810",
      "postalCode": "******000",
      "city": "Rio ** *******",
      "state": "RJ",
      "country": "BRA",
      "street": "Rua *** *****nte",
      "number": "***",
      "neighborhood": "Bot*****",
      "complement": "*** ** *",
      "reference": null
    }
  ],
  "logisticsInfo": [
    {
      "itemIndex": 0,
      "selectedSla": ".Transportadora",
      "slas": [
        {
          "id": ".Transportadora",
          "name": ".Transportadora",
          "deliveryIds": [
            {
              "courierId": "67",
              "warehouseId": "1_1",
              "dockId": "1_1_1",
              "courierName": "Transportadora",
              "quantity": 1
            }
          ],
          "shippingEstimate": "3d",
          "shippingEstimateDate": null,
          "lockTTL": null,
          "availableDeliveryWindows": [],
          "deliveryWindow": null,
          "price": 956,
          "tax": 0
        }, {
          "id": "Agendada",
          "name": "Agendada",
          "deliveryIds": [
            {
              "courierId": "FA02F72F-FEBD-41A0-AF70-83A77E8C77A0",
              "warehouseId": "1_1",
              "dockId": "1_1_1",
              "courierName": "Entrega agendada",
              "quantity": 1
            }
          ],
          "shippingEstimate": "90d",
          "shippingEstimateDate": null,
          "lockTTL": null,
          "availableDeliveryWindows": [
            {
              "startDateUtc": "2014-04-21T09:00:00+00:00",
              "endDateUtc": "2014-04-21T12:00:00+00:00",
              "price": 1000,
              "tax": 0
            }, {
              "startDateUtc": "2014-04-21T13:00:00+00:00",
              "endDateUtc": "2014-04-21T17:00:00+00:00",
              "price": 1000,
              "tax": 0
            }
          ],
          "deliveryWindow": null,
          "price": 1220,
          "tax": 0
        }
      ]
    }
  ]
}
```

### paymentData

Un objeto que contiene:

- `availableAccounts`: un array de objetos **availableAccount**. Cada **availableAccount** contiene información sobre una cuenta de pago disponible para uso del cliente.  

- `giftCards`: um array de objetos **giftCard**. Cada **giftCard** contiene información sobre un certificado de regalo disponible para usar con la compra.  

- `installmentOptions`: un array de objetos:  

  - `paymentSystem`: el **id** de **paymentSystem** a los que se aplican estas opciones de pago  

  - `value`: el valor  

  - `installments`: un array de objetos. Cada objeto representa una opción de cuotas para este sistema de pago, que contiene información como el número de cuotas, intereses y montos.  

- `paymentSystems`: un array de objetos **paymentSystem**. Cada **paymentSystem** contiene información como identificadores, tipo, nombre y validadores de tarjetas de crédito.  
- `payments`: un array de objetos de **payments**. Cada **payment** contiene información sobre el método de pago activo, como el monto del pago, el monto del pago sin intereses, el número de cuotas elegidas, el sistema de pago, el BIN de la tarjeta y el ID de la cuenta (identificación de la tarjeta guardada).


```json
{
  "giftCards": [
    {
      "redemptionCode": "HYUO-TEZZ-QFFT-HTFR",
      "value": 500,
      "balance": 500,
      "name": null,
      "id": "-1390324156495k195pmab4rall3di",
      "inUse": true,
      "isSpecialCard": false
    }, {
      "redemptionCode": "MTHU-WNTD-VXJW-TIDC",
      "value": 0,
      "balance": 700000,
      "name": "loyalty-program",
      "id": "122",
      "inUse": false,
      "isSpecialCard": true
    }
  ],
  "availableAccounts": [
    {
      "accountId": "71F2775D46BF44B1BF217F828F4E6131",
      "paymentSystem": "2",
      "paymentSystemName": "Visa",
      "cardNumber": "************1111",
      "availableAddresses": ["-1363804954758", "-1366200971560"]
    }
  ],
  "installmentOptions": [
    {
      "paymentSystem": "2",
      "value": 16175,
      "installments": [
        {
          "count": 1,
          "hasInterestRate": false,
          "interestRate": 0,
          "value": 16175,
          "total": 16175
        }, {
          "count": 2,
          "hasInterestRate": false,
          "interestRate": 132,
          "value": 4178,
          "total": 16712
        }
      ]
    }
  ],
  "paymentSystems": [
    {
      "id": 2,
      "name": "Visa",
      "groupName": "creditCardPaymentGroup",
      "validator": {
        "regex": "^4",
        "mask": "9999 9999 9999 9999",
        "cardCodeRegex": "[^0-9]",
        "cardCodeMask": "999",
        "weights": [2, 1, 2, 1, 2, 1, 2, 1, 2, 1, 2, 1, 2, 1, 2, 1, 2, 1, 2]
      },
      "stringId": null,
      "template": "creditCardPaymentGroup-template",
      "requiresDocument": false,
      "selected": false,
      "isCustom": false,
      "description": null
    }
  ],
  "payments": [
    {
      "accountId": null,
      "bin: null,
      "installments": 2,
      "paymentSystem": "12",
      "referenceValue": 16175,
      "value": 16175
    }
  ]
}
```

### sellers

Es un array de objetos **seller**. Cada **seller** tiene información simple sobre un vendedor que opera en el mercado de la tienda.


```json
[
  {
    "id": "1",
    "name": "meuamigopet",
    "logo": "http://portal.vtexcommerce.com.br/arquivos/logo.jpg"
  }
]
```

### messages

Un array de mensajes relacionados con la llamada realizada a la API.


```json
[
  {
    "code": null,
    "status": "error",
    "text": "O vale compra de código AAAA-BBBB-CCCC-DDDD não foi encontrado no sistema"
  }
]
```

### clientPreferencesData

Un pequeño objeto que contiene las preferencias del cliente.


```json
{
  "attachmentId": "clientPreferencesData",
  "locale": "pt-BR",
  "optinNewsLetter": true
}
```

### storePreferencesData

Un objeto simple que contiene las preferencias de la tienda.


```json
{
  "countryCode": "BRA",
  "checkToSavePersonDataByDefault": true,
  "templateOptions": {
    "toggleCorporate": false
  },
  "timeZone": "E. South America Standard Time",
  "currencyCode": "BRL",
  "currencyLocale": 0,
  "currencySymbol": "R$",
  "currencyFormatInfo": {
    "currencyDecimalDigits": 2,
    "currencyDecimalSeparator": ",",
    "currencyGroupSeparator": ".",
    "currencyGroupSize": 3,
    "startsWithCurrencySymbol": true
  }
}
```
