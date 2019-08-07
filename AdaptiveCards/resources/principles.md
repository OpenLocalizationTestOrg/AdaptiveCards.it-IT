---
title: Motivazioni e principi
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732563"
---
# <a name="motivations-and-principles"></a>Motivazioni e principi

Di seguito sono riportati i principi e le motivazioni govering l'evoluzione del formato di scheda adattivo.

## <a name="motivations-behind-the-format"></a>Motivazioni dietro il formato

Nei primi 2016, diversi team di Microsoft (tra cui Outlook, Windows e bot Framework) hanno avuto la consapevolezza che tutti volevano qualcosa di molto simile ("carte") e che ognuno di essi progettava soluzioni personalizzate in modo indipendente:

- Windows aveva i riquadri animati e il formato delle notifiche
-  Bot Framework usa un set di modelli di scheda predefiniti che gli sviluppatori possono scegliere quando inviano messaggi bot
- Outlook usa il proprio formato MessageCard per la funzionalità dei messaggi di utilità pratica

Allo stesso tempo, altre piattaforme, ad esempio LINE, FaceBook Messenger, slack e altre, definivano il proprio formato "card" proprietario. Quindi, alcuni dipendenti Microsoft si sono raccolti e hanno iniziato a impegnarsi per definire un singolo formato di scheda aperto e un set di SDK che:

- Semplifica l'interscambio delle schede tra gli host
- Consentire a ogni host di mantenere il controllo dello stile delle schede per garantire la coerenza visiva
- Consente a un'applicazione host di visualizzare facilmente le schede con il minimo sforzo tramite SDK pronti per l'uso
- E che fornirebbe anche valore a terze parti e, infine, sarà ampiamente adottato dal settore

## <a name="principles-governing-adaptive-cards"></a>Principi che governano le schede adattive

1.  **Adaptive Card è un formato di scheda _semplice_ e dichiarativo**

    1.  Non è concepito come sostituzione/alternativa HTML o XAML
    2.  Non esiste **alcuna "code-behind"** con schede adattive
        1. Gli autori di schede non possono incorporare codice personalizzato/arbitrario con i relativi payload e, di conseguenza, un host di schede adattivo non deve mai eseguire codice di terze parti
        2. Dinamismo e interattività vengono realizzati esclusivamente tramite markup dichiarativo
    3.  In questo modo si garantisce che lo sforzo necessario per creare un SDK per schede adattivo per una nuova piattaforma rimanga ragionevole

2.  **Il formato di scheda adattivo non può imporre l'utilizzo di una particolare tecnologia sottostante**

    1.  Il formato della scheda adattiva non si basa su JavaScript C#,, Python o qualsiasi altro linguaggio
    2.  Analogamente, non si basa su HTML o XAML o su qualsiasi altro Framework grafico/interfaccia utente
    3.  In questo modo, le schede adattive possono essere renderizzate in modo nativo in qualsiasi piattaforma finché esiste un renderer

3.  **Il formato della scheda Adaptive è una _proprietà condivisa_**

    1.  Insieme ai relativi SDK, il formato deve essere open source e il suo sviluppo basato su community
    2.  Il formato non è quindi di proprietà né è gestito da un team

4.  **Il formato di scheda adattivo non è progettato "solo per l'uso da parte di Microsoft"**

    1.  È invece progettato per soddisfare le esigenze di un'ampia gamma di applicazioni e casi d'uso

5.  **Il _gruppo di lavoro della scheda adattivo_ regola l'evoluzione del formato**

    1.  Questo gruppo di lavoro è costituito da un set di dipendenti Microsoft che sono tutti profondamente interessati al successo del formato
    2.  Il gruppo di lavoro effettua riunioni settimanali (attualmente il lunedì) durante le quali vengono esaminate le proposte di funzionalità, i problemi aperti sono discussi e sono stati rilevati i problemi e lo stato di avanzamento generale degli elementi di lavoro vNext
    3.  Il gruppo di lavoro usa il feedback della community di grandi dimensioni, inclusi i team interni di Microsoft, per decidere come evolvere il formato
        1. Chiunque può partecipare al gruppo di lavoro tramite l'apertura di problemi in GitHub (vedere di seguito)
        2. Le richieste di problemi/funzionalità con radice nell'utilizzo effettivo del framework delle schede adattive (come host o autore della scheda) hanno il maggiore effetto sul futuro del formato
    4.  Per essere approvata dal gruppo di lavoro, sono state proposte nuove funzionalità:
        1. Deve essere giustificato da casi d'uso reali
        2. Deve avere una specifica funzionale
    5.  Le nuove funzionalità approvate vengono aggiunte al backlog e considerate per vNext
        1. I criteri usati per definire la priorità delle nuove funzionalità includono l'ampia gamma di scenari abilitati dalla funzionalità, la complessità e la gestibilità e altro ancora
        2. In caso di dubbi, è opportuno tenerlo fuori. È molto più semplice introdurre una funzionalità ben progettata più avanti rispetto a un errore per sempre.
    6.  Tutte le nuove funzionalità sono implementate in tutti gli SDK supportati
    7.  Tutte le nuove funzionalità sono documentate e associate a una scheda di test pubblicata nella cartella Samples
    8.  Le nuove versioni del formato e degli SDK passano attraverso una fase beta
    9.  La pianificazione del rilascio per lo schema delle schede adattivo e le versioni dell'SDK è basata sulla qualità, non sulla data

6.  **Interoperabilità**
    1.  Le schede create in base al formato documentato, ad esempio non usando alcuna estensione specifica dell'host, verranno renderizzate correttamente in qualsiasi host con supporto per schede adattivo
    2.  Le uniche eccezioni a questi principi sono:
        1.  Alcuni host potrebbero non consentire l'interattività e pertanto non eseguiranno il rendering di input né azioni
        2.  L'esecuzione dell'azione. l'invio di azioni è a discrezione dell'host e non tutti gli host gestiranno necessariamente correttamente tutti i payload Action. Submit. Inoltre, alcuni host potrebbero non supportare Action. Submit

7.  **Il formato deve essere estendibile**

    1.  Gli host devono avere la libertà di aggiungere il supporto per elementi personalizzati o azioni personalizzate che vanno oltre il formato in grado di supportare
    2.  Questa operazione è particolarmente importante per le azioni, in quanto i vari host non supportano necessariamente lo stesso set di azioni
    3.  Queste aggiunte sono a discrezione dell'host
        1. Non sono un'aggiunta di fatto alla specifica della scheda adattiva
        2. Di conseguenza, rendono un payload che li usa incompatibile con il formato di scheda adattivo mainstream
        3. Tuttavia, possono essere presentate al gruppo di lavoro e proposte come nuove funzionalità per una versione futura del formato, come descritto in Point #5

8.  **Gli autori di schede sono proprietari del contenuto, le app host possiedono l'aspetto**

    1.  Le app host impongono lo stile, quindi le schede hanno un aspetto analogo alle estensioni native dell'esperienza dell'app
    2.  Gli autori di schede possono comunque specificare lo stile, ma solo tramite espressioni semantiche di colori, dimensioni e così via.

9.  **Verranno forniti gli SDK per le piattaforme di sviluppo più diffuse**

    1.  Gli SDK semplificano il rendering dei payload adattivi delle schede in qualsiasi host
    2.  Ciò garantisce che la barriera all'ingresso sia il più basso possibile per gli sviluppatori di terze parti e i team Microsoft
