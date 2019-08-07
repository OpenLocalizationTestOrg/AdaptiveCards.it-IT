---
title: Host config - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34d28ef0f0cd7200965fb6967bb2f252f6a47456
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732933"
---
# <a name="host-config---ios"></a>Configurazione host-iOS

L'host può essere configurato tramite HostConfig che può essere generato da una stringa JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

È possibile creare un'istanza di HostConfig predefinito

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Eseguire il rendering di una scheda usando la configurazione host

Rederer accetta la configurazione dell'host e della scheda adattiva. HostConfig può essere null e, se Nil, verrà usato il valore predefinito.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```