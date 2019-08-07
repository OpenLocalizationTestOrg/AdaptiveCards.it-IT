---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733008"
---
# <a name="getting-started---android"></a><span data-ttu-id="8a284-102">Guida introduttiva-Android</span><span class="sxs-lookup"><span data-stu-id="8a284-102">Getting started - Android</span></span>

<span data-ttu-id="8a284-103">Si tratta di un renderer che è destinato ai controlli nativi Android.</span><span class="sxs-lookup"><span data-stu-id="8a284-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="8a284-104">Installare il pacchetto Maven</span><span class="sxs-lookup"><span data-stu-id="8a284-104">Install Maven package</span></span>

<span data-ttu-id="8a284-105">[![Maven centrale](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="8a284-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="8a284-106">È possibile trovare i pacchetti pubblicati</span><span class="sxs-lookup"><span data-stu-id="8a284-106">You can find the published packages</span></span> ![qui](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="8a284-108">Per includere la libreria nel progetto, è necessario includere questa riga nel progetto Gradle. Build nella sezione dipendenze</span><span class="sxs-lookup"><span data-stu-id="8a284-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="8a284-109">È necessario modificare il numero di versione in base alla versione che si vuole includere nel progetto</span><span class="sxs-lookup"><span data-stu-id="8a284-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="8a284-110">Aggiungi importazione</span><span class="sxs-lookup"><span data-stu-id="8a284-110">Add import</span></span>

<span data-ttu-id="8a284-111">Per includere il modello a oggetti, aggiungere questa importazione</span><span class="sxs-lookup"><span data-stu-id="8a284-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="8a284-112">Per includere il renderer, aggiungere questa importazione</span><span class="sxs-lookup"><span data-stu-id="8a284-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="8a284-113">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8a284-113">Next steps</span></span>

<span data-ttu-id="8a284-114">Vedere [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.</span><span class="sxs-lookup"><span data-stu-id="8a284-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
