---
title: Schede adattive per sviluppatori Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c9ea788cfbc8e365cdece1cd8f42c3718b7bc3e7
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733118"
---
# <a name="adaptive-cards-for-windows-developers"></a>Schede adattive per sviluppatori Windows



## <a name="timeline"></a>Sequenza temporale

La prima esperienza di Windows per supporta le schede adattive è la sequenza temporale, una nuova esperienza introdotta per la prima volta in Windows 10 1803. 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a>API UserActivity

L' [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API è il modo in cui popola un'attività in sequenza temporale.

La scheda adattiva verrà fornita tramite la `Content` proprietà di, come illustrato di `VisualElement`seguito:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>Altre informazioni

Questa sessione alla build 2017 illustra le attività degli utenti in detial.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Altre superfici di Windows
Non è ancora presente alcuna azione da condividere, ma stiamo lavorando per incorporare le schede adattive in altre esperienze di Windows.

## <a name="dive-in"></a>Approfondimenti

In questa esercitazione la superficie non è stata rilasciata, quindi è possibile consultare i collegamenti riportati di seguito per approfondire le proprie informazioni sulle schede adattive.

* [Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione
* Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per apprendere gli elementi disponibili
* Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti
