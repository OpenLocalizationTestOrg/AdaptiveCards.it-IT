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
# <a name="tools-and-samples"></a><span data-ttu-id="77a7e-102">Strumenti ed esempi</span><span class="sxs-lookup"><span data-stu-id="77a7e-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="77a7e-103">Progettazione schede</span><span class="sxs-lookup"><span data-stu-id="77a7e-103">Card Designer</span></span> 

<span data-ttu-id="77a7e-104">Serve uno strumento per progettare le tue schede?</span><span class="sxs-lookup"><span data-stu-id="77a7e-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="77a7e-105">La finestra di progettazione delle schede Adaptive basata su browser è disponibile all'indirizzo[https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="77a7e-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="77a7e-106">[![schermata della finestra di progettazione](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="77a7e-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="77a7e-107">Incorporare la finestra di progettazione nell'app</span><span class="sxs-lookup"><span data-stu-id="77a7e-107">Embed the designer into your app</span></span>

<span data-ttu-id="77a7e-108">Ma perché inviare gli utenti quando è possibile **incorporare la finestra di progettazione delle schede direttamente nell'app Web** usando la libreria JavaScript.</span><span class="sxs-lookup"><span data-stu-id="77a7e-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="77a7e-109">Per iniziare, vedere il pacchetto di [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) .</span><span class="sxs-lookup"><span data-stu-id="77a7e-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="77a7e-110">Convalida dello schema</span><span class="sxs-lookup"><span data-stu-id="77a7e-110">Schema validation</span></span>

<span data-ttu-id="77a7e-111">La convalida dello schema è un modo efficace per semplificare la creazione e abilitare gli strumenti.</span><span class="sxs-lookup"><span data-stu-id="77a7e-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="77a7e-112">È stato fornito un [file di schema JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) completo per la modifica e la convalida di schede adattive in JSON.</span><span class="sxs-lookup"><span data-stu-id="77a7e-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="77a7e-113">Si noti che l'URL dello schema è con versione, le versioni più recenti delle schede adattive avranno un URL corrispondente.</span><span class="sxs-lookup"><span data-stu-id="77a7e-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="77a7e-114">In Visual Studio e Visual Studio Code è possibile ottenere IntelliSense automatico includendo un `$schema` riferimento.</span><span class="sxs-lookup"><span data-stu-id="77a7e-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![completamento automatico](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="77a7e-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="77a7e-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="77a7e-118">Estensione Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="77a7e-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="77a7e-119">È stata creata un'estensione di Visual Studio Code che consente di visualizzare la scheda che si sta modificando in tempo reale all'interno dell'editor.</span><span class="sxs-lookup"><span data-stu-id="77a7e-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![estensione](media/tools/vscode-extension.png)

<span data-ttu-id="77a7e-121">Per installare, aprire Extensions Marketplace e cercare **Visualizzatore Adaptive Card**.</span><span class="sxs-lookup"><span data-stu-id="77a7e-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![mercato](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="77a7e-123">Utilizzo</span><span class="sxs-lookup"><span data-stu-id="77a7e-123">Usage</span></span>

<span data-ttu-id="77a7e-124">Quando si modifica un file con estensione JSON con una proprietà della scheda `$schema` adattiva, è possibile visualizzare `Ctrl+Shift+V A`tramite.</span><span class="sxs-lookup"><span data-stu-id="77a7e-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="77a7e-125">Opzioni</span><span class="sxs-lookup"><span data-stu-id="77a7e-125">Options</span></span>

<span data-ttu-id="77a7e-126">Per il Visualizzatore AdaptiveCards è disponibile la seguente impostazione Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="77a7e-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="77a7e-127">Questa impostazione può essere configurata nelle impostazioni utente o nelle impostazioni dell'area di lavoro.</span><span class="sxs-lookup"><span data-stu-id="77a7e-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="77a7e-128">Esempio di visualizzatore WPF</span><span class="sxs-lookup"><span data-stu-id="77a7e-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="77a7e-129">Il [progetto di esempio visualizzatore WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) consente di visualizzare le schede utilizzando WPF/XAML in un computer Windows.</span><span class="sxs-lookup"><span data-stu-id="77a7e-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="77a7e-130">Un `hostconfig` Editor è integrato per la modifica e la visualizzazione delle impostazioni di configurazione host.</span><span class="sxs-lookup"><span data-stu-id="77a7e-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="77a7e-131">Salvare queste impostazioni come JSON per usarle nel rendering nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="77a7e-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualizzatore WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="77a7e-133">Esempio di ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="77a7e-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="77a7e-134">Il [progetto di esempio ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) converte qualsiasi scheda in un png dalla riga di comando tramite WPF.</span><span class="sxs-lookup"><span data-stu-id="77a7e-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
