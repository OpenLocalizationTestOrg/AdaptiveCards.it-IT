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
# <a name="text-features"></a><span data-ttu-id="1146a-102">Funzionalità di testo</span><span class="sxs-lookup"><span data-stu-id="1146a-102">Text features</span></span>

<span data-ttu-id="1146a-103">`TextBlock`in sono disponibili alcune funzionalità avanzate per la formattazione e la localizzazione del testo.</span><span class="sxs-lookup"><span data-stu-id="1146a-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="1146a-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="1146a-104">Markdown</span></span>
<span data-ttu-id="1146a-105">Per supportare il markup inline, le schede adattive supportano un **subset** della sintassi Markdown.</span><span class="sxs-lookup"><span data-stu-id="1146a-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="1146a-106">_Supportato_</span><span class="sxs-lookup"><span data-stu-id="1146a-106">_Supported_</span></span>

| <span data-ttu-id="1146a-107">Stile testo</span><span class="sxs-lookup"><span data-stu-id="1146a-107">Text Style</span></span>      | <span data-ttu-id="1146a-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="1146a-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="1146a-109">**Grassetto**</span><span class="sxs-lookup"><span data-stu-id="1146a-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="1146a-110">_Corsivo_</span><span class="sxs-lookup"><span data-stu-id="1146a-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="1146a-111">Elenco Bullet</span><span class="sxs-lookup"><span data-stu-id="1146a-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="1146a-112">Elenco numerato</span><span class="sxs-lookup"><span data-stu-id="1146a-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="1146a-113">Collegamenti ipertestuali</span><span class="sxs-lookup"><span data-stu-id="1146a-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="1146a-114">_Non supportato_</span><span class="sxs-lookup"><span data-stu-id="1146a-114">_Not supported_</span></span>

* <span data-ttu-id="1146a-115">Intestazioni</span><span class="sxs-lookup"><span data-stu-id="1146a-115">Headers</span></span>
* <span data-ttu-id="1146a-116">Tabelle</span><span class="sxs-lookup"><span data-stu-id="1146a-116">Tables</span></span>
* <span data-ttu-id="1146a-117">Immagini</span><span class="sxs-lookup"><span data-stu-id="1146a-117">Images</span></span>
* <span data-ttu-id="1146a-118">Qualsiasi elemento non presente nella tabella precedente</span><span class="sxs-lookup"><span data-stu-id="1146a-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="1146a-119">Esempio di Markdown</span><span class="sxs-lookup"><span data-stu-id="1146a-119">Markdown Example</span></span>

<span data-ttu-id="1146a-120">Il payload seguente produrrebbe un risultato simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1146a-120">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="1146a-122">Formattazione e localizzazione di data/ora</span><span class="sxs-lookup"><span data-stu-id="1146a-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="1146a-123">A volte non si conosce il fuso orario dell'utente che riceve la scheda, quindi le schede `DATE()` adattive offrono e `TIME()` formattano le funzioni per localizzare automaticamente l'ora sul dispositivo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1146a-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="1146a-124">Esempio di data/ora</span><span class="sxs-lookup"><span data-stu-id="1146a-124">Date/Time Example</span></span>

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

<span data-ttu-id="1146a-125">Verrà visualizzata la scheda precedente:</span><span class="sxs-lookup"><span data-stu-id="1146a-125">The above card will display:</span></span> 

> <span data-ttu-id="1146a-126">**Il pacchetto arriverà il Mar, il 14 febbraio 2017 alle 6:00**</span><span class="sxs-lookup"><span data-stu-id="1146a-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="1146a-127">Regole delle funzioni di data/ora</span><span class="sxs-lookup"><span data-stu-id="1146a-127">Date/Time function rules</span></span>

<span data-ttu-id="1146a-128">Esistono alcune regole per interpretare correttamente le funzioni di data/ora in ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="1146a-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="1146a-129">Se le regole non vengono soddisfatte, la stringa non elaborata verrà visualizzata all'utente e nessuno lo desidera.</span><span class="sxs-lookup"><span data-stu-id="1146a-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="1146a-130">**distinzione maiuscole** /minuscole (deve essere tutti i limiti)</span><span class="sxs-lookup"><span data-stu-id="1146a-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="1146a-131">**Nessuno spazio** tra le `{{`parentesi `}}`, o</span><span class="sxs-lookup"><span data-stu-id="1146a-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="1146a-132">\*\*Formattazione Strict [RFC 3389](https://tools.ietf.org/html/rfc3339) \*\* (Vedere gli esempi riportati di seguito)</span><span class="sxs-lookup"><span data-stu-id="1146a-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="1146a-133">**Deve essere** una data e un'ora valide</span><span class="sxs-lookup"><span data-stu-id="1146a-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="1146a-134">Formati validi</span><span class="sxs-lookup"><span data-stu-id="1146a-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="1146a-135">Parametro di formattazione della data</span><span class="sxs-lookup"><span data-stu-id="1146a-135">Date formatting param</span></span>

<span data-ttu-id="1146a-136">Per le date, è possibile specificare un parametro facoltativo per formattare l'output.</span><span class="sxs-lookup"><span data-stu-id="1146a-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="1146a-137">Formato</span><span class="sxs-lookup"><span data-stu-id="1146a-137">Format</span></span>        |            <span data-ttu-id="1146a-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="1146a-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="1146a-139">`COMPACT`Predefinita</span><span class="sxs-lookup"><span data-stu-id="1146a-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="1146a-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="1146a-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="1146a-141">"Lun, 13 feb, 2017"</span><span class="sxs-lookup"><span data-stu-id="1146a-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="1146a-142">"Lunedì 13 febbraio 2017"</span><span class="sxs-lookup"><span data-stu-id="1146a-142">"Monday, February 13th, 2017"</span></span> |

