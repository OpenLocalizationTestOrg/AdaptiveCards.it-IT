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
# <a name="host-config---android"></a>Configurazione host-Android

Per personalizzare il renderer, fornire un'istanza dell'oggetto HostConfig. Per la descrizione completa, vedere [schema di configurazione host](../../../rendering-cards/host-config.md) .

Per creare un oggetto HostConfig da una stringa, usare il Metodo DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```