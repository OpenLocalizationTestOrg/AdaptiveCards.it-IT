---
title: Strumenti per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f0c5a61d3406e1defffefc575ee0a6ec78fba93d
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733028"
---
# <a name="tools-and-samples"></a>Strumenti ed esempi

## <a name="card-designer"></a>Progettazione schede 

Serve uno strumento per progettare le tue schede? La finestra di progettazione delle schede Adaptive basata su browser è disponibile all'indirizzo[https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![schermata della finestra di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Incorporare la finestra di progettazione nell'app

Ma perché inviare gli utenti quando è possibile **incorporare la finestra di progettazione delle schede direttamente nell'app Web** usando la libreria JavaScript. 

Per iniziare, vedere il pacchetto di [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) .

## <a name="schema-validation"></a>Convalida dello schema

La convalida dello schema è un modo efficace per semplificare la creazione e abilitare gli strumenti.

È stato fornito un [file di schema JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) completo per la modifica e la convalida di schede adattive in JSON. Si noti che l'URL dello schema è con versione, le versioni più recenti delle schede adattive avranno un URL corrispondente.

In Visual Studio e Visual Studio Code è possibile ottenere IntelliSense automatico includendo un `$schema` riferimento.

![bad](media/tools/invalidjson1.png)

![completamento automatico](media/tools/autocomplete.png)

## <a name="example"></a>Esempio

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a>Estensione Visual Studio Code

È stata creata un'estensione di Visual Studio Code che consente di visualizzare la scheda che si sta modificando in tempo reale all'interno dell'editor. 

![estensione](media/tools/vscode-extension.png)

Per installare, aprire Extensions Marketplace e cercare **Visualizzatore Adaptive Card**.

![mercato](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Utilizzo

Quando si modifica un file con estensione JSON con una proprietà della scheda `$schema` adattiva, è possibile visualizzare `Ctrl+Shift+V A`tramite.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Opzioni

Per il Visualizzatore AdaptiveCards è disponibile la seguente impostazione Visual Studio Code. Questa impostazione può essere configurata nelle impostazioni utente o nelle impostazioni dell'area di lavoro.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Esempio di visualizzatore WPF

Il [progetto di esempio visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede utilizzando WPF/XAML in un computer Windows.  Un `hostconfig` Editor è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host. Salvare queste impostazioni come JSON per usarle nel rendering nell'applicazione.

![visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Esempio di ImageRender WPF

Il [progetto di esempio ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) converte qualsiasi scheda in un png dalla riga di comando tramite WPF. 
