---
title: Rendering di schede all'interno dell'applicazione
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732608"
---
# <a name="rendering-cards-inside-your-application"></a>Rendering di schede all'interno dell'applicazione

È facile eseguire il rendering di schede adattive all'interno dell'applicazione. Sono disponibili SDK per tutte le piattaforme comuni, oltre a fornire una [specifica dettagliata](implement-a-renderer.md) per la creazione di un renderer di schede adattivo personalizzato.

1. **Installare un RENDERER SDK** per la piattaforma di destinazione.
2. **Creare un'istanza di renderer** , configurata con lo stile, le regole e i gestori eventi di azione dell'app.
3. **Eseguire il rendering di una scheda nell'interfaccia utente nativa** : viene automaticamente applicato lo stile all'app.

## <a name="adaptive-cards-sdks"></a>SDK per schede adattive

|Piattaforma|Installazione di|Compilazione|Docs|Stato|
|---|---|---|---|---|
| JavaScript | [![installazione di NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Documenti](../sdk/rendering-cards/javascript/getting-started.md) | ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Documenti](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Documenti](../sdk/rendering-cards/net-html/getting-started.md) | ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Documenti](../sdk/rendering-cards/uwp/getting-started.md) | ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven centrale](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Documenti](../sdk/rendering-cards/android/getting-started.md) | ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Origine](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Documenti](../sdk/rendering-cards/ios/getting-started.md) |  ![Stato compilazione](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Creare un'istanza del renderer

Il passaggio successivo consiste nel creare un'istanza di un `AdaptiveCardRenderer`oggetto. 

### <a name="hook-up-action-events"></a>Associa eventi azione

Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti sulla scheda, ma spetta all'app fare in modo che si comportino come previsto. Ogni SDK è equivalente a un `OnAction` evento che è necessario gestire.

* **Action. OpenURL** : apre l'oggetto `url`specificato.  
* **Action. Submit** : consente di portare il risultato dell'invio e di inviarlo all'origine. Il modo in cui viene inviato all'origine della scheda è interamente all'utente.
* **Action. ShowCard** : richiama una finestra di dialogo ed esegue il rendering della sottoscheda in tale finestra di dialogo. Si noti che è necessario gestire questa impostazione solo `ShowCardActionMode` se è impostato `popup`su.

## <a name="render-a-card"></a>Eseguire il rendering di una scheda

Dopo aver acquisito il payload di una scheda, è sufficiente chiamare il renderer e passare la scheda. Verrà restituito un oggetto di interfaccia utente nativo costituito dal contenuto della scheda. A questo punto, è sufficiente inserire questa interfaccia utente nell'app.

## <a name="customization"></a>Personalizzazione

Esistono diversi modi per personalizzare gli elementi di cui viene eseguito il rendering. 

### <a name="hostconfig"></a>HostConfig

Un [Hostconfig](host-config.md) è un oggetto di configurazione multipiattaforma condiviso che controlla lo stile di base e il comportamento delle schede all'interno dell'app. Definisce elementi come le dimensioni dei caratteri, la spaziatura tra elementi, colori, il numero di azioni supportate e così via. 

### <a name="native-platform-styling"></a>Stile della piattaforma nativa

La maggior parte dei framework dell'interfaccia utente consente di applicare uno stile alla scheda sottoposta a rendering utilizzando lo stile nativo dell'interfaccia utente. In HTML, ad esempio, è possibile specificare le classi CSS per il codice HTML oppure in XAML è possibile passare un oggetto ResourceDictionary personalizzato per un controllo con granularità fine dell'output.

### <a name="customize-per-element-rendering"></a>Personalizzare il rendering per elemento

Ogni SDK consente di eseguire l'override del rendering di qualsiasi elemento o persino di aggiungere il supporto per elementi completamente nuovi definiti dall'utente.  Ad esempio, è possibile modificare il `Input.Date` renderer per emettere un controllo personalizzato mantenendo comunque il resto dell'output del renderer. In alternativa, è possibile aggiungere il supporto `Rating` per un elemento personalizzato definito dall'utente.



