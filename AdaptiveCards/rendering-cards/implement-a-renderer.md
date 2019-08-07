---
title: Implementazione di un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732613"
---
# <a name="adaptive-card-renderer-specification"></a>Specifica del renderer di schede adattive

Nella specifica seguente viene descritto come implementare un renderer di schede adattivo su qualsiasi piattaforma dell'interfaccia utente.

> [!IMPORTANT]
> 
> Il contenuto non è ancora terminato. Tornare a breve.

## <a name="sdk-versioning"></a>Controllo delle versioni dell'SDK

1. La versione principale e secondaria dell'SDK **deve** corrispondere `schema` alla versione. 
1. Patch/Build **deve** essere usato per gli aggiornamenti del renderer che non hanno modifiche dello schema.

## <a name="parsing-json"></a>Analisi di JSON

### <a name="error-conditions"></a>Condizioni di errore
1. Un parser **deve** verificare che sia contenuto JSON valido
1. Un parser **deve** convalidare lo schema (proprietà obbligatorie e così via)
1. Gli errori precedenti **devono** essere segnalati all'app host (eccezione o equivalente)

### <a name="unknown-types"></a>Tipi sconosciuti
1. Se vengono rilevati "tipi" sconosciuti, è **necessario eliminarli** dal risultato
1. Eventuali modifiche del payload (come sopra) **devono** essere segnalate come avvisi all'app host

### <a name="unknown-properties"></a>Proprietà sconosciute
1. Un parser **deve** includere proprietà **aggiuntive** sugli elementi

### <a name="additional-considerations"></a>Ulteriori considerazioni
1. La `speak` proprietà può contenere il markup SSML e **deve** essere restituita all'app host come specificato

## <a name="parsing-host-config"></a>Analisi della configurazione dell'host
1. TODO

## <a name="versioning"></a>Controllo delle versioni

1. Un renderer **deve** implementare una particolare versione dello schema. 
1. Il `AdaptiveCard` costruttore **deve** fornire alla `version` proprietà un valore predefinito in base alla versione dello schema corrente. 
1. Se un renderer rileva `version` una proprietà `AdaptiveCard` in maggiore della versione supportata, **deve** invece restituire l'oggetto `fallbackText` .

## <a name="rendering"></a>Rendering

Un `AdaptiveCard` oggetto è costituito `actions`da un oggetto `body` e da. È una raccolta di `CardElement`oggetti che un renderer enumera e esegue il rendering nell'ordine. `body` 

1. Ogni elemento **deve** estendersi alla larghezza del padre (think `display: block` in HTML).
1. Un renderer **deve** ignorare i tipi di elemento sconosciuti e continuare a eseguire il rendering del resto del payload.

### <a name="spacing-and-separators"></a>Spaziatura e separatori

1. La `spacing` proprietà di ogni elemento influisce sulla quantità di spazio tra l'elemento **corrente** e quello **precedente** .
1. La spaziatura deve essere applicata **solo** quando esiste effettivamente un elemento che la precede. (Ad esempio, non si applica al primo elemento di una matrice)
1. Un renderer **deve** cercare la quantità di spazio da usare dalla `hostConfig` spaziatura per il valore enum applicato all'elemento corrente.
1. Se l'elemento ha un `separator` `true`valore, sarà **necessario** tracciare una riga visibile tra l'elemento corrente e quello precedente.
1. La linea di separazione **deve** essere disegnata `container.style.default.foregroundColor`utilizzando.
1. È necessario disegnare un separatore **solo** se l'elemento **non è** il primo nella matrice.

### <a name="columns"></a>Colonne

1. `Column`Deve essere interpretato da "auto", "Stretch" o da un rapporto ponderato. `width`

### <a name="textblock"></a>TextBlock

1. Un TextBlock **deve** assumere una sola riga, a meno che `wrap` la proprietà `true`non sia. 
1. Il blocco di testo **deve** tagliare qualsiasi testo in eccesso con i puntini di sospensione (...)

#### <a name="markdown"></a>Markdown

1. Le schede adattive consentono un subset di Markdown e **devono** essere supportate in `TextBlock`. 
1. Vedere i [requisiti Markdown](../authoring-cards/text-features.md) completi

#### <a name="formatting-functions"></a>Funzioni di formattazione

1. `TextBlock`consente le [funzioni di formattazione di data/ora](../authoring-cards/text-features.md) che **devono** essere supportate in ogni renderer.
1. **Tutti gli errori devono** visualizzare la stringa non elaborata nella scheda. Nessun messaggio descrittivo provato. (L'obiettivo è quello di rendere lo sviluppatore immediatamente in grado di riconoscere la presenza di un problema)

1. TODO: Includi Regex

### <a name="images"></a>Immagini

1. Un renderer **deve** consentire alle app host di rilevare il momento in cui tutte le immagini http sono state scaricate e la scheda è "completamente sottoposta a rendering"
1. Un renderer **deve** controllare il param config `maxImageSize` dell'host durante il download delle immagini http
1. Un renderer **deve** supportare `.png` e`.jpeg`
1. Un renderer **deve** supportare `.gif` le immagini

### <a name="host-config"></a>Configurazione host

* TODO: Quali sono le impostazioni predefinite? Tutte le condivisioni? È necessario incorporare un file hostConfig. JSON comune nei file binari?
* TODO: Credo che anche HostConfig debba essere sottoposto a controllo delle versioni per l'analisi?

[`HostConfig`](host-config.md)è un oggetto di configurazione condivisa che specifica il modo in cui un renderer di schede adattivo genera l'interfaccia utente.  

Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer su piattaforme e dispositivi diversi. Consente inoltre di creare strumenti che offrono un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.

1. I renderer **devono** esporre un parametro di **Configurazione host** per le app host
1. Tutti gli elementi **devono** avere uno stile in base alle rispettive impostazioni di configurazione host

### <a name="native-platform-styling"></a>Stile della piattaforma nativa

1. Ogni tipo di elemento **deve** associare uno stile di piattaforma nativo con l'elemento dell'interfaccia utente generato. Ad esempio, in HTML è stata aggiunta una classe CSS ai tipi di elemento e in XAML viene assegnato uno stile specifico.

## <a name="extensibility"></a>Estendibilità 

1. Un renderer **deve** consentire alle app host di eseguire l'override di renderer di elementi predefiniti. Ad esempio, sostituire `TextBlock` il rendering con la propria logica.
1. Un renderer **deve** consentire alle app host di registrare tipi di elementi personalizzati. Ad esempio, aggiungere il supporto per un `Rating` elemento personalizzato
1. Un renderer **deve** consentire alle app host di rimuovere il supporto per un elemento predefinito. Ad esempio, rimuovere `Action.Submit` se non si vuole che sia supportata.

## <a name="actions"></a>Azioni

1. Se Hostconfig `supportsInteractivity` è `false`, un renderer **non deve** eseguire il rendering di alcuna azione.
1. La `actions` proprietà **deve** essere sottoposta a rendering come pulsanti in un certo tipo di barra delle azioni, in genere nella parte inferiore della scheda. 
1. Quando si tocca un pulsante, è **necessario** consentire all'app host di gestire l'evento. 
1. L'evento **deve** passare tutte le proprietà associate con l'azione
1. L'evento **deve** passare lungo l' `AdaptiveCard` oggetto che è stato eseguito

Azione | Comportamento
--- | ---
**Action.OpenUrl** | Aprire un URL esterno per la visualizzazione
**Action.ShowCard** | Richiede che una scheda secondaria venga visualizzata all'utente.
**Action.Submit** | Chiedere a tutti gli elementi di input di essere raccolti in un oggetto che viene quindi inviato tramite un metodo definito dall'applicazione host.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl`**Deve** aprire un URL usando il meccanismo della piattaforma nativa
1. Se questo non è possibile, **deve** generare un evento nell'app host per gestire l'apertura dell'URL. Questo evento **deve** consentire all'app host di eseguire l'override del comportamento predefinito. Ad esempio, consente di aprire l'URL all'interno della propria app.

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard`**Deve** essere supportato in qualche modo, in base all'impostazione hostConfig. Sono disponibili due modalità: inline e popup. Le schede inline **devono** impostare la visibilità della scheda automaticamente. In modalità popup, un evento **deve** essere generato nell'app host per mostrare la scheda in qualche modo.

### <a name="actionsubmit"></a>Action.Submit

L'azione di invio si comporta come un modulo HTML submit, ad eccezione del fatto che, nel caso in cui il codice HTML attivi un post HTTP, le schede adattive lo lasciano a ogni app host per determinare il significato "Submit". 

1. Quando **deve** generare un evento, l'utente tocca l'azione richiamata.  
1. La `data` proprietà **deve** essere inclusa nel payload di callback.
1. Per `Action.Submit`, un renderer **deve** raccogliere tutti gli input sulla scheda e recuperare i relativi valori. 

### <a name="selectaction"></a>selectAction

1. `supportedInteractivity` Se la `false` configurazione host è quindi, non è necessario eseguire il rendering come destinazione tocco. `selectAction`
1. `Image`, `ColumnSet`e `Column` offrono una`selectAction` proprietà, che **deve** essere eseguita quando viene richiamata dall'utente, ad esempio, toccando l'elemento.

## <a name="inputs"></a>Input

1. Se Hostconfig `supportsInteractivity` è `false` un renderer **non deve** eseguire il rendering degli input.
2. Gli input **devono** essere sottoposte a rendering con la massima fedeltà possibile. Un oggetto `Input.Date` , ad esempio, offrirebbe idealmente una selezione data a un utente, ma se questo non è possibile nello stack dell'interfaccia utente, il renderer **deve** eseguire il fallback per il rendering di una casella di testo standard.
3. Un renderer **dovrebbe** visualizzare `placeholderText` , se possibile
4. **Non** è necessario che un renderer implementi la convalida dell'input. Gli utenti di schede adattive devono pianificare la convalida dei dati ricevuti alla fine.
5. Il valore di input **deve** essere preceduto da un carattere di escape

6. L'oggetto **deve** essere restituito all'app host nel modo seguente:

   Non viene eseguita alcuna promessa di convalida dell'input nelle schede adattive, pertanto spetta all'entità ricevente analizzare correttamente la risposta. Ad esempio, un input. Number può restituire "Hello" ed è necessario prepararlo.


## <a name="events"></a>Eventi

1. Un renderer **deve** generare un evento quando la visibilità di un elemento è cambiata, consentendo all'app host di scorrere la scheda in posizione.
