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
# <a name="getting-started---javascript"></a><span data-ttu-id="7e8a7-102">Guida introduttiva-JavaScript</span><span class="sxs-lookup"><span data-stu-id="7e8a7-102">Getting started - JavaScript</span></span>

<span data-ttu-id="7e8a7-103">Come descritto in [Introduzione](../../../authoring-cards/getting-started.md) pagina, una scheda adattiva è un modello a oggetti della scheda serializzato JSON.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="7e8a7-104">Si tratta di un SDK JavaScript per la generazione di HTML sul lato client nel browser.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e8a7-105">**Modifiche di rilievo da v 0,5**</span><span class="sxs-lookup"><span data-stu-id="7e8a7-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="7e8a7-106">Il pacchetto è stato rinominato da `microsoft-adaptivecards` a`adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="7e8a7-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="7e8a7-107">Lo stato `AdaptiveCards.setHostConfig()` statico è stato spostato in un membro di `AdaptiveCard`istanza di.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="7e8a7-108">E.g., `myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="7e8a7-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="7e8a7-109">`HostConfig`è stata rinominata e spostata diverse.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="7e8a7-110">Vedere la configurazione host [Sample. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) per la struttura corrente</span><span class="sxs-lookup"><span data-stu-id="7e8a7-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="7e8a7-111">Sono state apportate anche alcune modifiche dello schema rispetto alla versione 0.5 Preview, [descritte qui](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="7e8a7-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="7e8a7-112">La funzione `renderCard()` statica è stata rimossa perché era ridondante con i metodi della classe.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="7e8a7-113">Usare `adaptiveCard.render()` come descritto di seguito.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="7e8a7-114">Installazione di</span><span class="sxs-lookup"><span data-stu-id="7e8a7-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="7e8a7-115">Nodo</span><span class="sxs-lookup"><span data-stu-id="7e8a7-115">Node</span></span>

<span data-ttu-id="7e8a7-116">[![installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="7e8a7-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="7e8a7-117">RETE CDN</span><span class="sxs-lookup"><span data-stu-id="7e8a7-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="7e8a7-118">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="7e8a7-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="7e8a7-119">Importare il modulo</span><span class="sxs-lookup"><span data-stu-id="7e8a7-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="7e8a7-120">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="7e8a7-120">Next steps</span></span>

<span data-ttu-id="7e8a7-121">Vedere [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="7e8a7-121">See [Render a card](render-a-card.md) for the next steps!</span></span>
