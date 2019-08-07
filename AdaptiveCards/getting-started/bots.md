---
title: Schede adattive per sviluppatori bot
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: a50f2e6f145ae2c4571d6b20b61b9ad182ca7ba5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733168"
---
# <a name="adaptive-cards-for-bot-developers"></a>Schede adattive per sviluppatori bot

Le schede adattive sono un'ottima soluzione per i bot. Consentono di creare una scheda una volta e di renderla perfettamente all'interno di più app, come Microsoft teams, il proprio sito Web e altro ancora.

> [!NOTE]
> Skype non è supportato nell'anteprima corrente. Per la versione più recente, vedere la pagina [stato partner](../resources/partners.md) .

## <a name="try-it-out"></a>Prova

Fare clic sul collegamento seguente e [parlare con il bot Scuba](http://contososcubademo.azurewebsites.net/). Supponiamo `I'm looking for scuba` che ti aiuterà a prenotare il viaggio delle immersioni dei tuoi sogni.  

Tutte le risposte del bot vengono create con le schede adattive.

[![Screenshot di Scuba chat](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Ottenere il codice**: il codice [](https://github.com/matthidinger/ContosoScubaBot
) sorgente di Contoso Scuba bot completo è disponibile in GitHub.


## <a name="bot-framework-integration"></a>Integrazione di bot Framework

Con [bot Framework](https://dev.botframework.com/) è possibile scrivere un singolo bot in grado di comunicare con gli utenti in più "canali", ad esempio Skype, Microsoft teams, Facebook Messenger e così via.

## <a name="walkthrough"></a>Procedura dettagliata

È piuttosto semplice aggiungere una scheda adattiva al bot.

### <a name="step-0-start-with-a-basic-message"></a>Passaggio 0: Inizia con un messaggio di base

Ecco un payload standard di bot `message` Framework che può essere recapitato a qualsiasi canale e visualizzare il testo all'utente.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Passaggio 1: Aggiungere una scheda adattiva`attachment`

Per aggiungere una certa ricchezza oltre al solo testo, bot Framework ha un concetto `attachments`di. 

Si collegherà quindi una scheda adattiva che Visualizza il testo personalizzato.

![Scheda adattiva di base](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a>Passaggio 2: Creazione di schede ancora più avanzate 

Le schede adattive offrono molto più del semplice testo personalizzabile. 

È possibile: 

* Aggiungi `Images` alla scheda
* Organizzare i contenuti con `Containers` e`Columns`
* Aggiungi più tipi di`Actions`
* Raccolta `Input` dagli utenti
* Disporre di una scheda`show another card`
* [Vedere la pagina relativa a Esplora schema completo](http://adaptivecards.io/explorer/). 

## <a name="platform-sdks"></a>SDK della piattaforma

Se il bot è stato sviluppato con .NET o NodeJS, sono disponibili librerie che rendono ancora più semplice la creazione di schede adattive.

Piattaforma|Installazione di|Altre informazioni
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentazione .NET per bot Framework](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Documentazione NodeJS di bot Framework](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Stato del canale

Bot Framework consente di pubblicare il bot su più canali. Stiamo lavorando con diversi canali per fornire supporto completo per le schede adattive. Per la versione più recente, vedere la pagina [stato partner](../resources/partners.md) .


## <a name="dive-in"></a>Approfondimenti

In questa esercitazione è stata rilevata solo la superficie, quindi è possibile esaminare i collegamenti riportati di seguito per esplorare altri modi in cui le schede adattive possono migliorare il bot.

* [Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione
* Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per apprendere gli elementi disponibili
* Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti
