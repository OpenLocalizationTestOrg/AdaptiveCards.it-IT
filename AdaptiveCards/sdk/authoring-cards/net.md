---
title: .NET SDK per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 009ac262b40152d120ca626ce0dadc6983bc187c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733038"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="e0dd0-102">.NET SDK per la creazione di schede</span><span class="sxs-lookup"><span data-stu-id="e0dd0-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="e0dd0-103">Come descritto nella pagina [Introduzione](../../authoring-cards/getting-started.md) , una scheda adattiva è un modello a oggetti JSON.</span><span class="sxs-lookup"><span data-stu-id="e0dd0-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="e0dd0-104">La libreria .NET rende molto più semplice l'uso di tale JSON.</span><span class="sxs-lookup"><span data-stu-id="e0dd0-104">The .NET library makes working with that JSON much easier.</span></span>


## <a name="nuget-install"></a><span data-ttu-id="e0dd0-105">Installazione di NuGet</span><span class="sxs-lookup"><span data-stu-id="e0dd0-105">NuGet Install</span></span>
<span data-ttu-id="e0dd0-106">Il `AdaptiveCards` pacchetto NuGet fornisce tipi per l'uso di schede adattive in .NET</span><span class="sxs-lookup"><span data-stu-id="e0dd0-106">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="e0dd0-107">[![Installazione di NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="e0dd0-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="e0dd0-108">Esempio: Creare una AdaptiveCard e serializzarla in JSON</span><span class="sxs-lookup"><span data-stu-id="e0dd0-108">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="e0dd0-109">Questo esempio illustra come compilare una scheda adattiva usando oggetti standard C# e quindi serializzarla in JSON per il trasporto in transito.</span><span class="sxs-lookup"><span data-stu-id="e0dd0-109">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = new Uri("http://adaptivecards.io/content/cats/1.png")
});

// serialize the card to JSON
string json = card.ToJson();
```

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="e0dd0-110">Esempio: Analizzare un AdaptiveCard da JSON</span><span class="sxs-lookup"><span data-stu-id="e0dd0-110">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="e0dd0-111">Questo esempio illustra come analizzare un payload JSON in una scheda adattiva.</span><span class="sxs-lookup"><span data-stu-id="e0dd0-111">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="e0dd0-112">Questo semplifica la manipolazione del modello a oggetti o persino il rendering di schede adattive all'interno dell'app usando gli [SDK renderer](../../rendering-cards/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="e0dd0-112">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient();
    var response = await client.GetAsync("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```
