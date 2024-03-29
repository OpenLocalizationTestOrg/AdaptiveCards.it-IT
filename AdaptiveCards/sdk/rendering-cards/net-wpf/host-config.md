---
title: Configurazione host-.NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 65e68c2c3e7fa244ba790afc3749912937ea8470
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732728"
---
# <a name="host-config---net-wpf"></a>Configurazione host-WPF .NET

Una configurazione [host](../../../rendering-cards/host-config.md) è un oggetto di configurazione condiviso che tutti i renderer comprendono. Questo consente di definire stili comuni (ad esempio, la famiglia di caratteri, le dimensioni dei caratteri, la spaziatura predefinita) e i comportamenti, ad esempio il numero massimo di azioni, che verranno interpretate automaticamente da ogni renderer della piattaforma. 

L'obiettivo è che l'interfaccia utente nativa generata da ogni renderer della piattaforma sarà molto simile al lavoro minimo da parte dell'utente.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig()
{
    FontStyles = new FontStylesConfig()
    {
        Default = new FontStyleConfig()
        {
            FontFamily = "Consolas",
            FontSizes = {
                Small = 15,
                Default = 20,
                Medium = 25,
                Large = 30,
                ExtraLarge= 40
            }
        },
    }
};

// Or parse from JSON
renderer.HostConfig = AdaptiveHostConfig.FromJson(@"{
    ""fontStyles"": {
        ""default"": {
            ""fontFamily"": ""Consolas"",
            ""fontSizes"": {
                ""small"": 15,
                ""default"": 20,
                ""medium"": 25,
                ""large"": 30,
                ""extraLarge"": 40
            }
        }
    }}");
```
