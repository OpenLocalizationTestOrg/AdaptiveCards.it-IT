---
title: Configurazione host-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 2828a379d8fda151b1cfca51e5898135186333ae
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733013"
---
# <a name="host-config---android"></a><span data-ttu-id="49d3a-102">Configurazione host-Android</span><span class="sxs-lookup"><span data-stu-id="49d3a-102">Host config - Android</span></span>

<span data-ttu-id="49d3a-103">Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig.</span><span class="sxs-lookup"><span data-stu-id="49d3a-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="49d3a-104">Per la descrizione completa, vedere [schema di configurazione host](../../../rendering-cards/host-config.md) .</span><span class="sxs-lookup"><span data-stu-id="49d3a-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="49d3a-105">Per creare un oggetto HostConfig da una stringa, usare il Metodo DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="49d3a-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```