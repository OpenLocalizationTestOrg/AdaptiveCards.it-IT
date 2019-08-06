---
title: Gestione del riconoscimento vocale
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ea46a1c2c14a4cd2aded9672d7493561bbebbd16
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732618"
---
# <a name="handling-speech"></a>Gestione del riconoscimento vocale

Per supportare le schede adattive vocali, `speak` la proprietà contiene informazioni sulla modalità di lettura di una scheda a un utente.

Il tag vocale può essere annotato usando il [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx). SSML offre la possibilità di controllare la velocità, il tono e l'inflessione del discorso.  Consente anche di eseguire lo streaming di audio o di un flusso audio TTS dal proprio servizio, offrendo una grande quantità di personalizzazione.

Esistono due modelli per l'utilizzo delle proprietà Speak da un'applicazione host:
* **alla consegna** : quando viene recapitata una scheda, un client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.
* **su richiesta** : per supportare un modello di accessibilità più completo, lo schema supporta un tag Speak per ogni elemento.  
Questo consente ai client di leggere ogni elemento nei destinatari con i requisiti di accessibilità.

