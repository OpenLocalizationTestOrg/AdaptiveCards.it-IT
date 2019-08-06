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
# <a name="getting-started"></a>Introduzione 

Una scheda adattiva è un modello a oggetti scheda serializzato in JSON.

## <a name="adaptive-card-structure"></a>Struttura di schede adattive

La struttura di base di una scheda è la seguente:

* `AdaptiveCard`-L'oggetto radice descrive il AdaptiveCard stesso, incluso il trucco dell'elemento, le azioni, il modo in cui deve essere pronunciato e la versione dello schema necessaria per eseguirne il rendering.
* `body`-Il corpo della scheda è costituito da blocchi predefiniti noti come `elements`. Gli elementi possono essere composti in disposizioni quasi infinite per creare molti tipi di schede. 
* `actions`-Molte schede includono un set di azioni che possono essere eseguite da un utente. Questa proprietà descrive le azioni di cui viene in genere eseguito il rendering in una "barra delle azioni" nella parte inferiore.

### <a name="example-card"></a>Scheda di esempio

Questa scheda di esempio include una singola riga di testo seguita da un'immagine.

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

## <a name="type-property"></a>Proprietà`Type`

Ogni elemento ha una `type` proprietà che identifica il tipo di oggetto. Osservando la scheda precedente, è possibile vedere che sono presenti due elementi, `TextBlock` `Image`e.

Tutti gli elementi di una scheda adattiva sono sovrapposti verticalmente e si espandono in `display: block` base alla **larghezza dell'elemento padre** (think in HTML). Tuttavia, è possibile usare un `ColumnSet` oggetto per creare colonne affiancate di contenitori.

## <a name="adaptive-elements"></a>Elementi adattivi

Gli elementi più importanti sono:

* **TextBlock** : aggiunge un blocco di testo con proprietà per controllare l'aspetto del testo
* **Image** : aggiunge un'immagine con le proprietà per controllare l'aspetto dell'immagine

## <a name="container-elements"></a>Elementi contenitore

Le schede possono avere anche contenitori, che dispongono di una raccolta di elementi figlio.

* **Container** : definisce una raccolta di elementi
* **Columnstore/colonna** : definisce una raccolta di colonne. ogni colonna è un contenitore
* **Fact** -contenitore di fact
* **Imaget** -contenitore di immagini in modo che l'interfaccia utente possa mostrare l'esperienza della raccolta foto appropriata per una raccolta di immagini.

## <a name="input-elements"></a>Elementi di input

Gli elementi di input consentono di richiedere all'interfaccia utente nativa di compilare moduli semplici:

* **Input. Text** -ottiene il contenuto del testo dall'utente
* **Input. date** : ottenere una data dall'utente
* **Input. Time** : ottenere un'ora dall'utente
* **Input. Number** : ottenere un numero dall'utente
* **Input. choicet** : assegnare all'utente un set di scelte e selezionarlo
* **Input. alternare** : assegnare all'utente un'unica scelta tra due elementi e selezionarli

## <a name="actions"></a>Azioni

Azioni aggiungere pulsanti alla scheda. Questi possono eseguire varie azioni, ad esempio l'apertura di un URL o l'invio di dati.

* **Action. OpenURL** : il pulsante apre un URL esterno per la visualizzazione
* **Action. ShowCard** : richiede una scheda secondaria da visualizzare all'utente.
* **Action. Submit** : richiede che tutti gli elementi di input vengano raccolti in un oggetto che viene quindi inviato tramite un metodo definito dall'applicazione host.

> **Azione di esempio. Invia**: Con Skype, un'azione. Submit invierà all'bot un'attività bot Framework bot con la proprietà **value** contenente un oggetto con tutti i dati di input.

## <a name="learn-more"></a>Ulteriori informazioni

* [Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione
* Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per esplorare gli elementi disponibili
* Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/)
* [Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti
