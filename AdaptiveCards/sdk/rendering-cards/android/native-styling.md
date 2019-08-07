---
title: Stile nativo-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c3190fbb31480f92c774d233476436ee2cfc52b3
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733023"
---
# <a name="native-styling---android"></a><span data-ttu-id="3e020-102">Stile nativo-Android</span><span class="sxs-lookup"><span data-stu-id="3e020-102">Native styling - Android</span></span>

<span data-ttu-id="3e020-103">Lo stile nativo non è supportato nel renderer Android. v 1.2 introduce il supporto per l'applicazione di stili ad alcune proprietà:</span><span class="sxs-lookup"><span data-stu-id="3e020-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="3e020-104">Sentimento azione</span><span class="sxs-lookup"><span data-stu-id="3e020-104">Action Sentiment</span></span>

<span data-ttu-id="3e020-105">La valutazione delle azioni è inclusa nella **versione 1.2** e non supporta il maggior numero di stili delle altre versioni , l' implementazione di uno stile valido e l'aggiunta della riga seguente nel Styles. XML per il progetto</span><span class="sxs-lookup"><span data-stu-id="3e020-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="3e020-106">Azione inline</span><span class="sxs-lookup"><span data-stu-id="3e020-106">Inline Action</span></span>

<span data-ttu-id="3e020-107">Gli input di testo con un'azione inline consentono lo stile per l'azione di cui viene eseguito il rendering.</span><span class="sxs-lookup"><span data-stu-id="3e020-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="3e020-108">Questo consente di applicare lo stile all'azione come pulsante (adaptiveInlineAction) o come immagine (adaptiveInlineActionImage)</span><span class="sxs-lookup"><span data-stu-id="3e020-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="3e020-109">Tutti i nomi degli elementi devono essere conservati come illustrato qui perché il renderer Cerca i nomi esatti</span><span class="sxs-lookup"><span data-stu-id="3e020-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>
