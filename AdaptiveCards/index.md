---
title: Cenni preliminari sulle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d62bae9259a45dd828028e4f866d18fc75924b0c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733113"
---
# <a name="adaptive-cards-overview"></a>Cenni preliminari sulle schede adattive 

Le schede adattive sono un formato di scambio di schede aperto che consente agli sviluppatori di scambiare contenuto dell'interfaccia utente in modo comune e coerente.

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>Come funzionano

Gli [**autori di schede**](authoring-cards/getting-started.md) descrivono il contenuto come un semplice oggetto JSON. Il rendering del contenuto può quindi essere eseguito in modo nativo all'interno di un' [**applicazione host**](rendering-cards/getting-started.md), adattando automaticamente l'aspetto dell'host.

Ad esempio, contoso bot può creare una scheda adattiva tramite bot Framework e, quando viene recapitato a Skype, avrà un aspetto simile a una scheda Skype. Quando lo stesso payload viene inviato a Microsoft teams, avrà un aspetto simile a Microsoft teams. Poiché più app host iniziano a supportare le schede adattive, lo stesso payload si illuminerà automaticamente all'interno di queste applicazioni, pur continuando a essere completamente nativo per l'app.

Gli utenti vincono perché tutti hanno familiarità. Le app host vincono perché controllano l'esperienza utente. E gli autori di schede vincono perché i loro contenuti ottengono una copertura più ampia senza alcuna attività aggiuntiva.

## <a name="goals"></a>Obiettivi 

Gli obiettivi per le schede adattive sono:

* **Portatile** : per qualsiasi app, dispositivo e Framework dell'interfaccia utente
* **Open** -Libraries e schema sono open source e Shared
* **Basso costo** -facile da definire, facile da utilizzare
* Mirato espressivo alla lunga coda di contenuti che gli sviluppatori vogliono produrre
* **Puramente** dichiarativo: non è necessario o consentito codice
* Con **stile automatico** per le linee guida per l'esperienza utente e il marchio dell'applicazione host

## <a name="for-card-authors"></a>Per gli autori di schede
Le schede adattive sono ottime per gli autori di schede:

* **Uno schema** : si ottiene un singolo formato, riducendo al minimo il costo della creazione di una scheda e massimizzando il numero di posizioni che è possibile usare.
* **Espressione più ricca** : il contenuto può essere allineato in modo più accurato con le informazioni desiderate, perché è presente una tavolozza più ricca con cui disegnare.
* **Ampia copertura** : i contenuti funzioneranno in un set più ampio di applicazioni senza dover apprendere nuovi schemi.
* **Controlli di input** : la scheda può includere controlli di input per la raccolta di informazioni dall'utente che visualizza la scheda.
* **Strumenti migliori** : un ecosistema di schede aperto significa strumenti migliori condivisi da tutti gli utenti.

## <a name="for-experience-owners"></a>Per i proprietari dell'esperienza
Gli sviluppatori di app che desiderano accedere a un ecosistema di contenuto di terze parti apprezzeranno le schede adattive perché:

* **Esperienza utente coerente** : si garantisce un'esperienza coerente agli utenti, perché si è proprietari dello stile della scheda sottoposta a rendering.
* **Prestazioni native** : si ottengono prestazioni native in quanto destinate direttamente al Framework dell'interfaccia utente.
* Il contenuto **sicuro** viene fornito in payload sicuri, quindi non è necessario aprire il Framework dell'interfaccia utente per markup non elaborato e scripting.
* **Facile da implementare** : puoi ottenere le librerie di scaffale per integrarle facilmente in qualsiasi piattaforma supportata 
* **Documentazione gratuita** : è possibile risparmiare tempo perché non è necessario inventare, implementare e documentare uno schema proprietario.
* **Strumenti condivisi** : è possibile risparmiare tempo perché non è necessario creare strumenti personalizzati.

## <a name="core-design-principles"></a>Principi di progettazione principali 

Le schede adattive sono basate su un set di [principi guida](resources/principles.md) che risultano utili per tenere traccia della progettazione. 

### <a name="semantic-instead-of-pixel-perfect"></a>Semantica anziché pixel-perfetto
Il più possibile per i valori semantici e i concetti è più mirato rispetto al layout puro in pixel perfetto. Esempi di espressione semantica vengono visualizzati in colori, dimensioni e in elementi come factt e Imaget. Che consentono all'applicazione host di prendere decisioni migliori sull'aspetto effettivo.

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>Gli autori di schede possiedono il contenuto, l'app host è proprietaria dell'aspetto
Gli autori delle schede possiedono quello che desiderano, ma l'applicazione che lo Visualizza è proprietario dell'aspetto della scheda nel contesto dell'applicazione.

### <a name="keep-it-simple-but-expressive"></a>Mantenerlo semplice, ma espressivo
Si vuole che le schede adattive siano espressive e per utilizzo generico, ma non si vuole creare un Framework dell'interfaccia utente.  Lo scopo è quello di creare un livello intermedio che sia "abbastanza espressivo" nello stesso modo in cui Markdown è sufficientemente espressivo per i documenti.

Concentrandosi su un semplice ed espressivo, Markdown ha creato una descrizione semplice e coerente del contenuto del documento.  Allo stesso modo, si ritiene che le schede adattive possano creare un semplice strumento espressivo per descrivere il contenuto delle schede.

### <a name="when-in-doubt-keep-it-out"></a>In caso di dubbi, è opportuno tenerlo fuori
È più facile da aggiungere in un secondo momento, quindi è possibile vivere con un errore. Se ci si è rivelato che è opportuno aggiungere qualcosa o meno, è stato scelto di lasciarlo invariato.  È sempre più semplice aggiungere una proprietà rispetto a una legacy che non è supportata.


## <a name="build-2018-session"></a>Compila sessione 2018

La sessione seguente in Build 2018 presenta le schede adattive in bot, Cortana, Outlook e Windows. 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>
