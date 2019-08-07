---
title: JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 55360658d74ca384b0e6090631a7f5db463e968a
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732908"
---
# <a name="getting-started---javascript"></a>Guida introduttiva-JavaScript

Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON. Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.

> [!IMPORTANT]
> **Modifiche di rilievo da v 0,5**
> 
> 1. Il pacchetto è stato rinominato da `microsoft-adaptivecards` a`adaptivecards`
> 1. Lo stato `AdaptiveCards.setHostConfig()` statico è stato spostato in un membro di `AdaptiveCard`istanza di. E.g., `myCard.hostConfig = {}` 
> 1. `HostConfig`è stata rinominata e spostata diverse. Vedere la configurazione host [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) per la struttura corrente
> 1. Sono state apportate anche alcune modifiche dello schema rispetto alla versione 0.5 Preview, [descritte qui](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. La funzione `renderCard()` statica è stata rimossa perché era ridondante con i metodi della classe. Usare `adaptiveCard.render()` come descritto di seguito. 


## <a name="install"></a>Installazione di

### <a name="node"></a>Nodo

[![installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>RETE CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Utilizzo

### <a name="import-the-module"></a>Importare il modulo

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Passaggi successivi

Vedere [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.
