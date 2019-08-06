---
title: Eseguire il rendering di una scheda-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 5ced7a2217ef6ef475aa344d92ad2f5e567266f8
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733003"
---
# <a name="render-a-card---android"></a><span data-ttu-id="8cdc2-102">Eseguire il rendering di una scheda-Android</span><span class="sxs-lookup"><span data-stu-id="8cdc2-102">Render a card - Android</span></span>

<span data-ttu-id="8cdc2-103">Di seguito viene illustrato come eseguire il rendering di una scheda utilizzando la Android SDK.</span><span class="sxs-lookup"><span data-stu-id="8cdc2-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="8cdc2-104">Creare un'istanza dell'oggetto scheda adattivo dal testo JSON</span><span class="sxs-lookup"><span data-stu-id="8cdc2-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="8cdc2-105">**Modifiche di rilievo per v 1.2**</span><span class="sxs-lookup"><span data-stu-id="8cdc2-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="8cdc2-106">Il parametro ElementParserRegistration è stato modificato in ParseContext che include un oggetto ElementParserRegistration e un oggetto ActionParserRegistration</span><span class="sxs-lookup"><span data-stu-id="8cdc2-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="8cdc2-107">oppure</span><span class="sxs-lookup"><span data-stu-id="8cdc2-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="8cdc2-108">Eseguire il rendering di una scheda</span><span class="sxs-lookup"><span data-stu-id="8cdc2-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
