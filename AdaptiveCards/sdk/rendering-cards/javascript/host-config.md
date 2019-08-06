---
title: Host config - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: a011ffc43c2990cd8eb568b9f1c449cf541f9a70
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732898"
---
# <a name="host-config---javascript"></a><span data-ttu-id="d15c5-102">Configurazione host-JavaScript</span><span class="sxs-lookup"><span data-stu-id="d15c5-102">Host config - JavaScript</span></span>

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a><span data-ttu-id="d15c5-103">Personalizzazione</span><span class="sxs-lookup"><span data-stu-id="d15c5-103">Customization</span></span>

<span data-ttu-id="d15c5-104">Sono disponibili tre modi per personalizzare il rendering adattivo della scheda:</span><span class="sxs-lookup"><span data-stu-id="d15c5-104">There are 3 ways to customize the adaptive card rendering:</span></span> 
1. <span data-ttu-id="d15c5-105">Configurazione host</span><span class="sxs-lookup"><span data-stu-id="d15c5-105">Host Config</span></span>
2. <span data-ttu-id="d15c5-106">Stile CSS</span><span class="sxs-lookup"><span data-stu-id="d15c5-106">CSS styling</span></span>
3. <span data-ttu-id="d15c5-107">Rendering di elementi personalizzati</span><span class="sxs-lookup"><span data-stu-id="d15c5-107">Custom element rendering</span></span>

### <a name="hostconfig"></a><span data-ttu-id="d15c5-108">HostConfig</span><span class="sxs-lookup"><span data-stu-id="d15c5-108">HostConfig</span></span> 

<span data-ttu-id="d15c5-109">Una configurazione [host](../../../rendering-cards/host-config.md) è un oggetto di configurazione condiviso che tutti i renderer comprendono.</span><span class="sxs-lookup"><span data-stu-id="d15c5-109">A [Host Config](../../../rendering-cards/host-config.md) is a shared configuration object that all renderers understand.</span></span> <span data-ttu-id="d15c5-110">Questo consente di definire stili comuni (ad esempio, la famiglia di caratteri, le dimensioni dei caratteri, la spaziatura predefinita) e i comportamenti, ad esempio il numero massimo di azioni, che verranno interpretate automaticamente da ogni renderer della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="d15c5-110">This allows you to define common styles (e.g., font family, font sizes, default spacing) and behaviors (e.g., max number of actions) that will be automatically interpreted by each platform renderer.</span></span> 

<span data-ttu-id="d15c5-111">L'obiettivo è che l'interfaccia utente nativa generata da ogni renderer della piattaforma sarà molto simile al lavoro minimo da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d15c5-111">The goal is that the native UI generated by each platform renderer will look very similar with minimal work on your part.</span></span>

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```