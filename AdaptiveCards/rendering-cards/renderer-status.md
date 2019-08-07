---
title: Stato renderer
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 63426b2250407cc40af8c46975c10f57d1028a40
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733088"
---
# <a name="renderer-status"></a>Stato renderer
Le tabelle seguenti mostrano lo stato corrente di ogni renderer, in base alle rispettive versioni pubblicate pubbliche.

### <a name="parsing"></a>Analisi

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Restituisci errori di convalida | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analizza proprietà sconosciute | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendering delle schede

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Verificare la versione supportata | ✅ | ✅ | ✅ | ✅ | ✅  |
|Rendering dello schema completo | ✅ | ✅ | ✅ | ✅ | ✅ |
|Barra delle azioni di rendering | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignora elementi sconosciuti | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supporto configurazione host | ✅ | ✅ | ✅ | ✅ | ✅ |
|Stile della piattaforma nativa | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Rendering elementi

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Spaziatura e separatore | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Formattazione di data/ora TextBlock](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Supporto di TextBlock Markdown](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Supporto per input completo | ✅ | ✅ | ✅ | ✅ | ✅ |

\*Il renderer HTML non include il supporto Markdown incorporato per ridurre al minimo le dimensioni della libreria e consentire al consumo di applicazioni di usare il processore Markdown preferito. Il renderer HTML userà tuttavia automaticamente Markdown-it se viene caricato.

### <a name="extensibility"></a>Estendibilità

|Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Esegui override renderer elementi | ✅ | ✅ | ✅ | ✅ | ✅ |
|Renderer Aggiungi nuovo elemento | ✅ | ✅ | ✅ | ✅ | ✅ |
|Renderer di elementi Remove | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Esegui override/Aggiungi/Rimuovi renderer azione](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Azioni

| Funzionalità | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Supporto di Action. OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Supporto di Action. ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Azione. Invia supporto  | ✅ | ✅ | ✅ | ✅ | ✅  |
| supporto di selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Eventi

|       Funzionalità        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilità elemento modificata |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

