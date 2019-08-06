---
title: HostConfig per schede adattive
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 848ce3dd2ccca1f975dfd330c1c88292c753641d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733098"
---
# <a name="what-is-hostconfig"></a>Che cos'è HostConfig?
`HostConfig`è un **oggetto di configurazione multipiattaforma** che specifica il modo in cui un renderer di schede adattivo genera l'interfaccia utente.

Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer su piattaforme e dispositivi diversi. Consente inoltre di creare strumenti che offrono un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.

Vedere un esempio di [Hostconfig. JSON](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) per ottenere un feeling per il contenuto.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig)-Opzioni di livello superiore per`AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig)-Opzioni per `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig)-Controlla lo stile per i contenitori predefiniti e di enfasi
   * [`FactSetConfig`](#schema-factsetconfig)-Controlla la visualizzazione di `FactSet`s
   * [`FontSizesConfig`](#schema-fontsizesconfig)-Controlla le metriche delle dimensioni del carattere per diversi stili di testo
   * [`FontWeightsConfig`](#schema-fontweightsconfig)-Controlla le metriche del peso del carattere
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig)-Controlla i vari colori dei tipi di carattere
   * [`ImageSetConfig`](#schema-imagesetconfig)-Controlla come `ImageSet`vengono visualizzati i
   * [`ImageSizesConfig`](#schema-imagesizesconfig)-Controlli `Image` dimensioni
   * [`MediaConfig`](#schema-mediaconfig): Controlla la visualizzazione e il comportamento `Media` degli elementi
   * [`SeparatorConfig`](#schema-separatorconfig)-Controlla la modalità di visualizzazione degli separatori
   * [`ShowCardConfig`](#schema-showcardconfig)-Controlla il comportamento e lo stile di`Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig): Controlla il layout degli elementi
   * [`TextBlockConfig`](#schema-textblockconfig)-Parametri che controllano la visualizzazione del testo

# <a name="card-configuration"></a>Configurazione scheda

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Opzioni di livello superiore per`AdaptiveCards`

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| No, valore predefinito:`true`|Controlla se lo stile personalizzato è consentito|1.0
|**supportsInteractivity**|`boolean`| No, valore predefinito:`true`|Controllare se gli `Action`oggetti interattivi possono essere richiamati|1.0
|**imageBaseUrl**|`string`| No|URL di base da usare durante il caricamento delle risorse|1.0
|**fontFamily**|`string`| No, valore predefinito:`"Calibri"`|Tipo di carattere da utilizzare per il rendering del testo|1.0
|**actions**|`object`| No|Opzioni per `Action`s|1.0
|**adaptiveCard**|`object`| No|Opzioni di livello superiore per`AdaptiveCards`|1.0
|**containerStyles**|`object`| No|Controlla lo stile per i contenitori predefiniti e di enfasi|1.0
|**imageSizes**|`object`| No|Dimensioni `Image` dei controlli|1.0
|**imageSet**|`object`| No|Controlla come `ImageSet`vengono visualizzati i|1.0
|**factSet**|`object`| No|Controlla la visualizzazione di `FactSet`s|1.0
|**fontSizes**|`object`| No|Controlla le metriche delle dimensioni del carattere per diversi stili di testo|1.0
|**fontWeights**|`object`| No|Controlla le metriche del peso del carattere|1.0
|**spacing**|`object`| No|Controlla la disposizione degli elementi|1.0
|**separator**|`object`| No|Controlla la modalità di visualizzazione degli separatori|1.0
|**media**|`object`| No|Controlla la visualizzazione e il comportamento `Media` degli elementi|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Opzioni per `Action`s

|Proprietà|Type|Obbligatorio|DESCRIZIONE|Version|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| No, valore predefinito:`"horizontal"`|Controlla come sono disposti i pulsanti|1.0
|**actionAlignment**|`string`| No, valore predefinito:`"stretch"`|Controllare il layout dei pulsanti|1.0
|**buttonSpacing**|`integer`| No, valore predefinito:`10`|Controlla la quantità di spaziatura da usare tra i pulsanti|1.0
|**maxActions**|`integer`| No, valore predefinito:`5`|Controlla il numero di azioni consentite in totale|1.0
|**spacing**|`string`| No, valore predefinito:`"default"`|Controlla la spaziatura complessiva dell'elemento Action|1.0
|**showCard**|`object`| No|Controlla il comportamento e lo stile di`Action.ShowCard`|1.0
|**iconPlacement**|`string`| No, valore predefinito:`"aboveTitle"`|Controlla dove posizionare l'icona azione|1.0
|**iconSize**|`integer`| No, valore predefinito:`30`|Icona delle dimensioni dei controlli dell'azione|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Controlla lo stile per i contenitori predefiniti e di enfasi

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| No|Stile contenitore predefinito|1.0
|**emphasis**|`object`| No|Stile del contenitore da usare per l'enfasi|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Controlla la visualizzazione di `FactSet`s

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**title**|`object`| No, valore predefinito:`{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Parametri che controllano la visualizzazione del testo|1.0
|**value**|`object`| No, valore predefinito:`{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Parametri che controllano la visualizzazione del testo|1.0
|**spacing**|`integer`| No, valore predefinito:`10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Controlla le metriche delle dimensioni del carattere per diversi stili di testo

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, valore predefinito:`10`|Dimensioni del carattere piccole|1.0
|**default**|`integer`| No, valore predefinito:`12`|Dimensioni del carattere predefinite|1.0
|**medium**|`integer`| No, valore predefinito:`14`|Dimensioni medie carattere|1.0
|**large**|`integer`| No, valore predefinito:`17`|Dimensione carattere grande|1.0
|**extraLarge**|`integer`| No, valore predefinito:`20`|Dimensioni del carattere molto grandi|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Controlla le metriche del peso del carattere

|Proprietà|Type|Obbligatorio|DESCRIZIONE|Version|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| No, valore predefinito:`200`|&nbsp;|1.0
|**default**|`integer`| No, valore predefinito:`400`|&nbsp;|1.0
|**bolder**|`integer`| No, valore predefinito:`800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Controlla i vari colori dei tipi di carattere

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| No, valore predefinito:`{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| No, valore predefinito:`{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| No, valore predefinito:`{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| No, valore predefinito:`{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| No, valore predefinito:`{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| No, valore predefinito:`{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| No, valore predefinito:`{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Controlla come `ImageSet`vengono visualizzati i

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| No, valore predefinito:`"auto"`|Controlla il ridimensionamento delle singole immagini|1.0
|**maxImageHeight**|`integer`| No, valore predefinito:`100`|Vincola altezza immagine a questo valore|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Dimensioni `Image` dei controlli

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, valore predefinito:`80`|Valore dimensioni piccole immagine|1.0
|**medium**|`integer`| No, valore predefinito:`120`|Valore dimensioni medie immagine|1.0
|**large**|`integer`| No, valore predefinito:`180`|Valore dimensioni immagine grande|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Controlla la visualizzazione e il comportamento `Media` degli elementi

#### <a name="introduced-in-version-11"></a>Introdotta nella versione 1,1

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| No|URI dell'immagine da visualizzare quando il pulsante Riproduci non è stato richiamato|1.1
|**playButton**|`string`| No|Immagine da visualizzare come pulsante Riproduci|1.1
|**allowInlinePlayback**|`boolean`| No, valore predefinito:`true`|Indica se visualizzare i supporti inline o richiamare esternamente|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Controlla la modalità di visualizzazione degli separatori

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| No, valore predefinito:`1`|Spessore della linea di separazione|1.0
|**lineColor**|`string,null`| No, valore predefinito:`#B2000000`|Colore da usare per la linea di separazione del disegno|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Controlla il comportamento e lo stile di`Action.ShowCard`

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| No, valore predefinito:`"inline"`|Controlla la modalità di visualizzazione della scheda|1.0
|**style**|`object`| No, valore predefinito:`emphasis`|Controlla lo stile di un contenitore|1.0
|**inlineTopMargin**|`integer`| No, valore predefinito:`16`|Quantità di margine da usare per la visualizzazione della scheda|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Controlla la disposizione degli elementi

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| No, valore predefinito:`3`|Valore spaziatura ridotta|1.0
|**default**|`integer`| No, valore predefinito:`8`|Valore spaziatura predefinita|1.0
|**medium**|`integer`| No, valore predefinito:`20`|Valore di spaziatura media|1.0
|**large**|`integer`| No, valore predefinito:`30`|Valore spaziatura grande|1.0
|**extraLarge**|`integer`| No, valore predefinito:`40`|Valore di spaziatura molto grande|1.0
|**padding**|`integer`| No, valore predefinito:`20`|Valore di riempimento|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Parametri che controllano la visualizzazione del testo

|Proprietà|Type|Obbligatorio|Descrizione|Version|
|--------|----|--------|-----------|-------|
|**size**|`string`| No, valore predefinito:`"default"`|Dimensioni del carattere da usare quando una scheda non specifica|1.0
|**weight**|`string`| No, valore predefinito:`"normal"`|Spessore del carattere da usare quando una scheda non specifica|1.0
|**color**|`string`| No, valore predefinito:`"default"`|Colore del carattere da usare quando una scheda non specifica|1.0
|**isSubtle**|`boolean`| No, valore predefinito:`false`|Il testo deve essere impercettibile se una scheda non specifica|1.0
|**wrap**|`boolean`| No, valore predefinito:`true`|Se una scheda non specifica, deve eseguire il ritorno a capo del testo|1.0
|**maxWidth**|`integer`| No, valore predefinito:`0`|Larghezza massima da usare se una scheda non specifica|1.0
