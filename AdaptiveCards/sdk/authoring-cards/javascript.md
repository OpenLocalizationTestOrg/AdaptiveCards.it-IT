---
title: JavaScript SDK per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732553"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="838ba-102">JavaScript SDK per la creazione di schede</span><span class="sxs-lookup"><span data-stu-id="838ba-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="838ba-103">La libreria per la serializzazione di JSON è ancora in fase di sviluppo e i chilometraggio possono variare.</span><span class="sxs-lookup"><span data-stu-id="838ba-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="838ba-104">Come descritto in [Introduzione](../../authoring-cards/getting-started.md), una scheda adattiva non è nient'altro che un oggetto JSON serializzato di un modello a oggetti della scheda.</span><span class="sxs-lookup"><span data-stu-id="838ba-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="838ba-105">Per semplificare la manipolazione del modello a oggetti sono state definite alcune librerie che definiscono una gerarchia di classi fortemente tipizzata che è facile da serializzare/deserializzare JSON.</span><span class="sxs-lookup"><span data-stu-id="838ba-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="838ba-106">È possibile usare qualsiasi strumento per creare il file JSON della scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="838ba-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="838ba-107">Il `adaptivecards` pacchetto NPM definisce una libreria per l'uso di schede adattive in JavaScript</span><span class="sxs-lookup"><span data-stu-id="838ba-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="838ba-108">Per installare</span><span class="sxs-lookup"><span data-stu-id="838ba-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="838ba-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="838ba-109">Example</span></span>

<span data-ttu-id="838ba-110">L'API seguente mostra come costruire una scheda adattiva usando il modello a oggetti e come serializzarla in JSON.</span><span class="sxs-lookup"><span data-stu-id="838ba-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
