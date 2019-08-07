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
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="794eb-102">Schede adattive per sviluppatori Windows</span><span class="sxs-lookup"><span data-stu-id="794eb-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="794eb-103">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="794eb-103">Timeline</span></span>

<span data-ttu-id="794eb-104">La prima esperienza di Windows per supporta le schede adattive è la sequenza temporale, una nuova esperienza introdotta per la prima volta in Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="794eb-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Sequenza temporale](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="794eb-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="794eb-106">UserActivity API</span></span>

<span data-ttu-id="794eb-107">L' [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API è il modo in cui popola un'attività in sequenza temporale.</span><span class="sxs-lookup"><span data-stu-id="794eb-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="794eb-108">La scheda adattiva verrà fornita tramite la `Content` proprietà di, come illustrato di `VisualElement`seguito:</span><span class="sxs-lookup"><span data-stu-id="794eb-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="794eb-109">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="794eb-109">Learn more</span></span>

<span data-ttu-id="794eb-110">Questa sessione alla build 2017 illustra le attività degli utenti in detial.</span><span class="sxs-lookup"><span data-stu-id="794eb-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="794eb-111">Altre superfici di Windows</span><span class="sxs-lookup"><span data-stu-id="794eb-111">Other Windows Surfaces</span></span>
<span data-ttu-id="794eb-112">Non è ancora presente alcuna azione da condividere, ma stiamo lavorando per incorporare le schede adattive in altre esperienze di Windows.</span><span class="sxs-lookup"><span data-stu-id="794eb-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="794eb-113">Approfondimenti</span><span class="sxs-lookup"><span data-stu-id="794eb-113">Dive in!</span></span>

<span data-ttu-id="794eb-114">In questa esercitazione la superficie non è stata rilasciata, quindi è possibile consultare i collegamenti riportati di seguito per approfondire le proprie informazioni sulle schede adattive.</span><span class="sxs-lookup"><span data-stu-id="794eb-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="794eb-115">[Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="794eb-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="794eb-116">Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per apprendere gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="794eb-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="794eb-117">Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="794eb-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="794eb-118">[Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="794eb-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
