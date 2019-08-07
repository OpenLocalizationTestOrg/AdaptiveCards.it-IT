---
title: Azioni
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733108"
---
# <a name="actions"></a>Azioni

Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti sulla scheda, ma spetta all'app fare in modo che si comportino come previsto. Ogni SDK è equivalente a un `OnAction` evento che è necessario gestire.

* **Action. OpenURL** : apre l'oggetto `url`specificato.  
* **Action. Submit** : consente di portare il risultato dell'invio e di inviarlo all'origine. Il modo in cui viene inviato all'origine della scheda è interamente all'utente.
* **Action. ShowCard** : richiama una finestra di dialogo ed esegue il rendering della sottoscheda in tale finestra di dialogo. Si noti che è necessario gestire questa impostazione solo `ShowCardActionMode` se è impostato `popup`su.