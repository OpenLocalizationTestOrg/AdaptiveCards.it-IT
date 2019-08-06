---
title: Roadmap per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733093"
---
# <a name="future-work"></a>Lavoro futuro

Anche se abbiamo realizzato un ottimo progresso nella definizione di schede adattive, c'è ancora molto lavoro da fare. Ci auguriamo che attraverso le community di sviluppatori attive come botness e partner eccezionali, ad esempio slack e Kik, possiamo creare un grande ecosistema di schede multipiattaforma.

## <a name="roadmap"></a>Guida di orientamento

Qui è possibile vedere la [Roadmap corrente (non finale)](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Si noti che qualsiasi elemento qui è soggetto a modifiche e non è una garanzia di spedizione.

## <a name="future-ideas"></a>Idee future

Di seguito sono riportate alcune idee future, che sono semplicemente nella fase Brainstorm. Se si è interessati a una di queste informazioni, inviare un commento.

### <a name="great-looking-cards-from-data"></a>Ottime schede per i dati

Sappiamo che molti autori di schede dispongono già di dati ben definiti dietro le proprie carte. Il piano prevede l'esplorazione di un modello di modello che consenta la generazione di schede (lato server o lato client) in base ai dati e a un repository di modelli ben definiti e personalizzabili.

### <a name="make-cards-responsive"></a>Rendi le schede reattive

I layout delle schede devono essere reattivi nello spazio disponibile. Le schede adattive sono adattabili a dispositivi diversi, stili di UX e Framework dell'interfaccia utente, ma non sono ancora stati riattivati. Per gli elementi è necessario definire proprietà aggiuntive che consentano ai produttori di schede di fornire gli hint necessari alle librerie di rendering, in modo che possano modificare il layout in modo intelligente in modo da mantenere lo scopo della scheda.

### <a name="responsive-exploration"></a>Esplorazione reattiva

* Aggiungere una proprietà di **importanza** che annotare l'importanza del contenuto. È possibile eliminare contenuto meno importante per adattarlo allo spazio disponibile
* Aggiungere **vincoli** e proprietà dei **criteri** che descrivono come reagire quando non è possibile soddisfare i vincoli. 
  * Nascondi contenuto o Comprimi contenuto a dimensioni inferiori.
  * Aggiungere una soglia che, quando superata, viene `columnSet` modificata in carosello di colonne.

### <a name="new-element-types"></a>Nuovi tipi di elemento

* Mappe? -incorporare una mappa in una scheda con interattività o fallback a bitmap
* *Quali elementi si desiderano o sono necessari*?

### <a name="new-rendering-libraries"></a>Nuove librerie di rendering

* React?
* Xamarin?
* *Quali sono i Framework desiderati?*
