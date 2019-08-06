---
title: Introduzione
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732653"
---
# <a name="getting-started"></a><span data-ttu-id="a898b-102">Introduzione</span><span class="sxs-lookup"><span data-stu-id="a898b-102">Getting Started</span></span> 

<span data-ttu-id="a898b-103">Una scheda adattiva è un modello a oggetti scheda serializzato in JSON.</span><span class="sxs-lookup"><span data-stu-id="a898b-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="a898b-104">Struttura di schede adattive</span><span class="sxs-lookup"><span data-stu-id="a898b-104">Adaptive Card structure</span></span>

<span data-ttu-id="a898b-105">La struttura di base di una scheda è la seguente:</span><span class="sxs-lookup"><span data-stu-id="a898b-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="a898b-106">`AdaptiveCard`-L'oggetto radice descrive il AdaptiveCard stesso, incluso il trucco dell'elemento, le azioni, il modo in cui deve essere pronunciato e la versione dello schema necessaria per eseguirne il rendering.</span><span class="sxs-lookup"><span data-stu-id="a898b-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="a898b-107">`body`-Il corpo della scheda è costituito da blocchi predefiniti noti come `elements`.</span><span class="sxs-lookup"><span data-stu-id="a898b-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="a898b-108">Gli elementi possono essere composti in disposizioni quasi infinite per creare molti tipi di schede.</span><span class="sxs-lookup"><span data-stu-id="a898b-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="a898b-109">`actions`-Molte schede includono un set di azioni che possono essere eseguite da un utente.</span><span class="sxs-lookup"><span data-stu-id="a898b-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="a898b-110">Questa proprietà descrive le azioni di cui viene in genere eseguito il rendering in una "barra delle azioni" nella parte inferiore.</span><span class="sxs-lookup"><span data-stu-id="a898b-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="a898b-111">Scheda di esempio</span><span class="sxs-lookup"><span data-stu-id="a898b-111">Example Card</span></span>

<span data-ttu-id="a898b-112">Questa scheda di esempio include una singola riga di testo seguita da un'immagine.</span><span class="sxs-lookup"><span data-stu-id="a898b-112">This sample card which includes a single line of text followed by an image.</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a><span data-ttu-id="a898b-113">Proprietà`Type`</span><span class="sxs-lookup"><span data-stu-id="a898b-113">`Type` property</span></span>

<span data-ttu-id="a898b-114">Ogni elemento ha una `type` proprietà che identifica il tipo di oggetto.</span><span class="sxs-lookup"><span data-stu-id="a898b-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="a898b-115">Osservando la scheda precedente, è possibile vedere che sono presenti due elementi, `TextBlock` `Image`e.</span><span class="sxs-lookup"><span data-stu-id="a898b-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="a898b-116">Tutti gli elementi di una scheda adattiva sono sovrapposti verticalmente e si espandono in `display: block` base alla **larghezza dell'elemento padre** (think in HTML).</span><span class="sxs-lookup"><span data-stu-id="a898b-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="a898b-117">Tuttavia, è possibile usare un `ColumnSet` oggetto per creare colonne affiancate di contenitori.</span><span class="sxs-lookup"><span data-stu-id="a898b-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="a898b-118">Elementi adattivi</span><span class="sxs-lookup"><span data-stu-id="a898b-118">Adaptive Elements</span></span>

<span data-ttu-id="a898b-119">Gli elementi più importanti sono:</span><span class="sxs-lookup"><span data-stu-id="a898b-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="a898b-120">**TextBlock** : aggiunge un blocco di testo con proprietà per controllare l'aspetto del testo</span><span class="sxs-lookup"><span data-stu-id="a898b-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="a898b-121">**Image** : aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine</span><span class="sxs-lookup"><span data-stu-id="a898b-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="a898b-122">Elementi contenitore</span><span class="sxs-lookup"><span data-stu-id="a898b-122">Container elements</span></span>

<span data-ttu-id="a898b-123">Le schede possono avere anche contenitori, che dispongono di una raccolta di elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="a898b-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="a898b-124">**Container** : definisce una raccolta di elementi</span><span class="sxs-lookup"><span data-stu-id="a898b-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="a898b-125">**Columnstore/colonna** : definisce una raccolta di colonne. ogni colonna è un contenitore</span><span class="sxs-lookup"><span data-stu-id="a898b-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="a898b-126">**Fact** -contenitore di fact</span><span class="sxs-lookup"><span data-stu-id="a898b-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="a898b-127">**Imaget** -contenitore di immagini in modo che l'interfaccia utente possa mostrare l'esperienza della raccolta foto appropriata per una raccolta di immagini.</span><span class="sxs-lookup"><span data-stu-id="a898b-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="a898b-128">Elementi di input</span><span class="sxs-lookup"><span data-stu-id="a898b-128">Input elements</span></span>

<span data-ttu-id="a898b-129">Gli elementi di input consentono di richiedere all'interfaccia utente nativa di compilare moduli semplici:</span><span class="sxs-lookup"><span data-stu-id="a898b-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="a898b-130">**Input. Text** -ottiene il contenuto del testo dall'utente</span><span class="sxs-lookup"><span data-stu-id="a898b-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="a898b-131">**Input. date** : ottenere una data dall'utente</span><span class="sxs-lookup"><span data-stu-id="a898b-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="a898b-132">**Input. Time** : ottenere un'ora dall'utente</span><span class="sxs-lookup"><span data-stu-id="a898b-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="a898b-133">**Input. Number** : ottenere un numero dall'utente</span><span class="sxs-lookup"><span data-stu-id="a898b-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="a898b-134">**Input. choicet** : assegnare all'utente un set di scelte e selezionarlo</span><span class="sxs-lookup"><span data-stu-id="a898b-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="a898b-135">**Input. alternare** : assegnare all'utente un'unica scelta tra due elementi e selezionarli</span><span class="sxs-lookup"><span data-stu-id="a898b-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="a898b-136">Azioni</span><span class="sxs-lookup"><span data-stu-id="a898b-136">Actions</span></span>

<span data-ttu-id="a898b-137">Azioni aggiungere pulsanti alla scheda.</span><span class="sxs-lookup"><span data-stu-id="a898b-137">Actions add buttons to the card.</span></span> <span data-ttu-id="a898b-138">Questi possono eseguire varie azioni, ad esempio l'apertura di un URL o l'invio di dati.</span><span class="sxs-lookup"><span data-stu-id="a898b-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="a898b-139">**Action. OpenURL** : il pulsante apre un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="a898b-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="a898b-140">**Action. ShowCard** : richiede una scheda secondaria da visualizzare all'utente.</span><span class="sxs-lookup"><span data-stu-id="a898b-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="a898b-141">**Action. Submit** : richiede che tutti gli elementi di input vengano raccolti in un oggetto che viene quindi inviato tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="a898b-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="a898b-142">**Azione di esempio. Invia**: Con Skype, un'azione. Submit invierà all'bot un'attività bot Framework bot con la proprietà **value** contenente un oggetto con tutti i dati di input.</span><span class="sxs-lookup"><span data-stu-id="a898b-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="a898b-143">Ulteriori informazioni</span><span class="sxs-lookup"><span data-stu-id="a898b-143">Learn More</span></span>

* <span data-ttu-id="a898b-144">[Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="a898b-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="a898b-145">Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per esplorare gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="a898b-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="a898b-146">Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="a898b-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="a898b-147">[Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="a898b-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
