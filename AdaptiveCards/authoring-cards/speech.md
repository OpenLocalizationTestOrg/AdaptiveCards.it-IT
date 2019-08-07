---
title: Riconoscimento vocale e personalizzazione avanzata
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732668"
---
# <a name="speech-and-advanced-customization"></a>Riconoscimento vocale e personalizzazione avanzata
Viviamo in un'epoca di interazione vocale tramite servizi come Cortana.  Le schede adattive sono progettate dal primo giorno per supportare la sintesi vocale, abilitando scenari nuovi e completi.

Il `speak` tag consente di recapitare la scheda adattiva a un ambiente in cui una visualizzazione visiva non è un'esperienza primaria, ad esempio un dashboard auto durante la guida. 

## <a name="speak-property"></a>Speak (proprietà)
Per supportare il riconoscimento vocale, `speak` abbiamo una proprietà che contiene testo da pronunciare all'utente. Il testo può essere annotato tramite[SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)(Speech Synthesis Markup Language). SSML controlla la velocità, il tono e la flessione del discorso.  Consente anche di eseguire lo streaming di audio o di un flusso audio TTS dal proprio servizio, offrendo una grande flessibilità per la personalizzazione.

Esistono due modelli per l'utilizzo delle proprietà Speak da un'applicazione host:

* Alla **consegna** : quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.
* **Su richiesta** -per supportare un modello di accessibilità più completo, lo schema supporta un tag Speak per ogni elemento. Il client può leggere una proprietà Speak per ogni elemento nella scheda.

### <a name="examples"></a>Esempi

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Progettazione del contenuto vocale

Il contenuto progettato per la sintesi vocale è diverso dal contenuto progettato per la visualizzazione visiva. Quando si progetta una scheda, si sta progettando un'intera esperienza visiva per presentare le informazioni a un utente in modo che le riaccenda. Quando si progetta per la sintesi vocale, è opportuno pensare a come descrivere verbalmente il contenuto in modo che riaccenda l'utente.  
