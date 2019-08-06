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
# <a name="host-config---javascript"></a>Configurazione host-JavaScript

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

## <a name="customization"></a>Personalizzazione

Sono disponibili tre modi per personalizzare il rendering adattivo della scheda: 
1. Configurazione host
2. Stile CSS
3. Rendering di elementi personalizzati

### <a name="hostconfig"></a>HostConfig 

Una configurazione [host](../../../rendering-cards/host-config.md) è un oggetto di configurazione condiviso che tutti i renderer comprendono. Questo consente di definire stili comuni (ad esempio, la famiglia di caratteri, le dimensioni dei caratteri, la spaziatura predefinita) e i comportamenti, ad esempio il numero massimo di azioni, che verranno interpretate automaticamente da ogni renderer della piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generata da ogni renderer della piattaforma sarà molto simile al lavoro minimo da parte dell'utente.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```