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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="560b1-102">Schede adattive per sviluppatori bot</span><span class="sxs-lookup"><span data-stu-id="560b1-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="560b1-103">Le schede adattive sono un'ottima soluzione per i bot.</span><span class="sxs-lookup"><span data-stu-id="560b1-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="560b1-104">Consentono di creare una scheda una volta e di renderla perfettamente all'interno di più app, come Microsoft teams, il proprio sito Web e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="560b1-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="560b1-105">Skype non è supportato nell'anteprima corrente.</span><span class="sxs-lookup"><span data-stu-id="560b1-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="560b1-106">Per la versione più recente, vedere la pagina [stato partner](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="560b1-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="560b1-107">Prova</span><span class="sxs-lookup"><span data-stu-id="560b1-107">Try it out</span></span>

<span data-ttu-id="560b1-108">Fare clic sul collegamento seguente e [parlare con il bot Scuba](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="560b1-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="560b1-109">Supponiamo `I'm looking for scuba` che ti aiuterà a prenotare il viaggio delle immersioni dei tuoi sogni.</span><span class="sxs-lookup"><span data-stu-id="560b1-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="560b1-110">Tutte le risposte del bot vengono create con le schede adattive.</span><span class="sxs-lookup"><span data-stu-id="560b1-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="560b1-111">[![Screenshot di Scuba chat](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="560b1-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="560b1-112">**Ottenere il codice**: il codice [](https://github.com/matthidinger/ContosoScubaBot
) sorgente di Contoso Scuba bot completo è disponibile in GitHub.</span><span class="sxs-lookup"><span data-stu-id="560b1-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="560b1-113">Integrazione di bot Framework</span><span class="sxs-lookup"><span data-stu-id="560b1-113">Bot Framework Integration</span></span>

<span data-ttu-id="560b1-114">Con [bot Framework](https://dev.botframework.com/) è possibile scrivere un singolo bot in grado di comunicare con gli utenti in più "canali", ad esempio Skype, Microsoft teams, Facebook Messenger e così via.</span><span class="sxs-lookup"><span data-stu-id="560b1-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="560b1-115">Procedura dettagliata</span><span class="sxs-lookup"><span data-stu-id="560b1-115">Walkthrough</span></span>

<span data-ttu-id="560b1-116">È piuttosto semplice aggiungere una scheda adattiva al bot.</span><span class="sxs-lookup"><span data-stu-id="560b1-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="560b1-117">Passaggio 0: Inizia con un messaggio di base</span><span class="sxs-lookup"><span data-stu-id="560b1-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="560b1-118">Ecco un payload standard di bot `message` Framework che può essere recapitato a qualsiasi canale e visualizzare il testo all'utente.</span><span class="sxs-lookup"><span data-stu-id="560b1-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="560b1-119">Passaggio 1: Aggiungere una scheda adattiva`attachment`</span><span class="sxs-lookup"><span data-stu-id="560b1-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="560b1-120">Per aggiungere una certa ricchezza oltre al solo testo, bot Framework ha un concetto `attachments`di.</span><span class="sxs-lookup"><span data-stu-id="560b1-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="560b1-121">Si collegherà quindi una scheda adattiva che Visualizza il testo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="560b1-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="560b1-123">Passaggio 2: Creazione di schede ancora più avanzate</span><span class="sxs-lookup"><span data-stu-id="560b1-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="560b1-124">Le schede adattive offrono molto più del semplice testo personalizzabile.</span><span class="sxs-lookup"><span data-stu-id="560b1-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="560b1-125">È possibile:</span><span class="sxs-lookup"><span data-stu-id="560b1-125">You can:</span></span> 

* <span data-ttu-id="560b1-126">Aggiungi `Images` alla scheda</span><span class="sxs-lookup"><span data-stu-id="560b1-126">Add `Images` to your card</span></span>
* <span data-ttu-id="560b1-127">Organizzare i contenuti con `Containers` e`Columns`</span><span class="sxs-lookup"><span data-stu-id="560b1-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="560b1-128">Aggiungi più tipi di`Actions`</span><span class="sxs-lookup"><span data-stu-id="560b1-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="560b1-129">Raccolta `Input` dagli utenti</span><span class="sxs-lookup"><span data-stu-id="560b1-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="560b1-130">Disporre di una scheda`show another card`</span><span class="sxs-lookup"><span data-stu-id="560b1-130">Have one card `show another card`</span></span>
* <span data-ttu-id="560b1-131">[Vedere la pagina relativa a Esplora schema completo](http://adaptivecards.io/explorer/).</span><span class="sxs-lookup"><span data-stu-id="560b1-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="560b1-132">SDK della piattaforma</span><span class="sxs-lookup"><span data-stu-id="560b1-132">Platform SDKs</span></span>

<span data-ttu-id="560b1-133">Se il bot è stato sviluppato con .NET o NodeJS, sono disponibili librerie che rendono ancora più semplice la creazione di schede adattive.</span><span class="sxs-lookup"><span data-stu-id="560b1-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="560b1-134">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="560b1-134">Platform</span></span>|<span data-ttu-id="560b1-135">Installazione di</span><span class="sxs-lookup"><span data-stu-id="560b1-135">Install</span></span>|<span data-ttu-id="560b1-136">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="560b1-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="560b1-137">.NET</span><span class="sxs-lookup"><span data-stu-id="560b1-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="560b1-138">Documentazione .NET per bot Framework</span><span class="sxs-lookup"><span data-stu-id="560b1-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="560b1-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="560b1-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="560b1-140">Documentazione NodeJS di bot Framework</span><span class="sxs-lookup"><span data-stu-id="560b1-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="560b1-141">Stato del canale</span><span class="sxs-lookup"><span data-stu-id="560b1-141">Channel status</span></span>

<span data-ttu-id="560b1-142">Bot Framework consente di pubblicare il bot su più canali.</span><span class="sxs-lookup"><span data-stu-id="560b1-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="560b1-143">Stiamo lavorando con diversi canali per fornire supporto completo per le schede adattive.</span><span class="sxs-lookup"><span data-stu-id="560b1-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="560b1-144">Per la versione più recente, vedere la pagina [stato partner](../resources/partners.md) .</span><span class="sxs-lookup"><span data-stu-id="560b1-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="560b1-145">Approfondimenti</span><span class="sxs-lookup"><span data-stu-id="560b1-145">Dive in!</span></span>

<span data-ttu-id="560b1-146">In questa esercitazione è stata rilevata solo la superficie, quindi è possibile esaminare i collegamenti riportati di seguito per esplorare altri modi in cui le schede adattive possono migliorare il bot.</span><span class="sxs-lookup"><span data-stu-id="560b1-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="560b1-147">[Sfoglia le schede di esempio](http://adaptivecards.io/samples/) per l'ispirazione</span><span class="sxs-lookup"><span data-stu-id="560b1-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="560b1-148">Utilizzare [Esplora schema](http://adaptivecards.io/explorer) per apprendere gli elementi disponibili</span><span class="sxs-lookup"><span data-stu-id="560b1-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="560b1-149">Compilare una scheda usando il [Visualizzatore interattivo](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="560b1-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="560b1-150">[Entra in contatto](http://adaptivecards.io/connect) con i tuoi commenti e suggerimenti</span><span class="sxs-lookup"><span data-stu-id="560b1-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
