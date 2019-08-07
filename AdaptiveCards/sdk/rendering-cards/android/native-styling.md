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
# <a name="native-styling---android"></a>Stile nativo-Android

Lo stile nativo non è supportato nel renderer Android. v 1.2 introduce il supporto per l'applicazione di stili ad alcune proprietà:

## <a name="action-sentiment"></a>Sentimento azione

La valutazione delle azioni è inclusa nella **versione 1.2** e non supporta il maggior numero di stili delle altre versioni , l' implementazione di uno stile valido e l'aggiunta della riga seguente nel Styles. XML per il progetto

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Azione inline

Gli input di testo con un'azione inline consentono lo stile per l'azione di cui viene eseguito il rendering. Questo consente di applicare lo stile all'azione come pulsante (adaptiveInlineAction) o come immagine (adaptiveInlineActionImage)

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Tutti i nomi degli elementi devono essere conservati come illustrato qui perché il renderer Cerca i nomi esatti
