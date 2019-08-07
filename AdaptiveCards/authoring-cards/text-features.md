---
title: Funzionalità di testo
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732673"
---
# <a name="text-features"></a>Funzionalità di testo

`TextBlock`in sono disponibili alcune funzionalità avanzate per la formattazione e la localizzazione del testo.

## <a name="markdown"></a>Markdown
Per supportare il markup inline, le schede adattive supportano un **subset** della sintassi Markdown.

_Supportato_

| Stile testo      | Markdown |
|-----------------|-----|
| **Grassetto**        | ```**Bold**``` |
| _Corsivo_        | ```_Italic_``` |
| Elenco Bullet     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Elenco numerato   | ```1. Green\r2. Orange\r3. Blue``` |
| Collegamenti ipertestuali      | ```[Title](url)``` |

_Non supportato_

* Intestazioni
* Tabelle
* Immagini
* Qualsiasi elemento non presente nella tabella precedente

### <a name="markdown-example"></a>Esempio di Markdown

Il payload seguente produrrebbe un risultato simile al seguente:

![schermata Markdown](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Formattazione e localizzazione di data/ora

A volte non si conosce il fuso orario dell'utente che riceve la scheda, quindi le schede `DATE()` adattive offrono e `TIME()` formattano le funzioni per localizzare automaticamente l'ora sul dispositivo di destinazione.

### <a name="datetime-example"></a>Esempio di data/ora

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

Verrà visualizzata la scheda precedente: 

> **Il pacchetto arriverà il Mar, il 14 febbraio 2017 alle 6:00**

### <a name="datetime-function-rules"></a>Regole delle funzioni di data/ora

Esistono alcune regole per interpretare correttamente le funzioni di data/ora in ogni piattaforma. Se le regole non vengono soddisfatte, la stringa non elaborata verrà visualizzata all'utente e nessuno lo desidera.

1. **distinzione maiuscole** /minuscole (deve essere tutti i limiti)
1. **Nessuno spazio** tra le `{{`parentesi `}}`, o
1. **Formattazione Strict [RFC 3389](https://tools.ietf.org/html/rfc3339) ** (Vedere gli esempi riportati di seguito)
1. **Deve essere** una data e un'ora valide

### <a name="valid-formats"></a>Formati validi

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Parametro di formattazione della data

Per le date, è possibile specificare un parametro facoltativo per formattare l'output.


|       Formato        |            Esempio            |
|---------------------|-------------------------------|
| `COMPACT`Predefinita |          "2/13/2017"          |
|       `SHORT`       |     "Lun, 13 feb, 2017"     |
|       `LONG`        | "Lunedì 13 febbraio 2017" |

