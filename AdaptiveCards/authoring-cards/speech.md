---
title: Riconoscimento vocale e personalizzazione avanzata
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 468d090dff0511f40cb7e5eedc4f4a18fa12aa3c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732668"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="484e8-102">Riconoscimento vocale e personalizzazione avanzata</span><span class="sxs-lookup"><span data-stu-id="484e8-102">Speech and advanced customization</span></span>
<span data-ttu-id="484e8-103">Viviamo in un'epoca di interazione vocale tramite servizi come Cortana.</span><span class="sxs-lookup"><span data-stu-id="484e8-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="484e8-104">Le schede adattive sono progettate dal primo giorno per supportare la sintesi vocale, abilitando scenari nuovi e completi.</span><span class="sxs-lookup"><span data-stu-id="484e8-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="484e8-105">Il `speak` tag consente di recapitare la scheda adattiva a un ambiente in cui una visualizzazione visiva non è un'esperienza primaria, ad esempio un dashboard auto durante la guida.</span><span class="sxs-lookup"><span data-stu-id="484e8-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="484e8-106">Speak (proprietà)</span><span class="sxs-lookup"><span data-stu-id="484e8-106">Speak property</span></span>
<span data-ttu-id="484e8-107">Per supportare il riconoscimento vocale, `speak` abbiamo una proprietà che contiene testo da pronunciare all'utente.</span><span class="sxs-lookup"><span data-stu-id="484e8-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="484e8-108">Il testo può essere annotato tramite[SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)(Speech Synthesis Markup Language).</span><span class="sxs-lookup"><span data-stu-id="484e8-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="484e8-109">SSML controlla la velocità, il tono e la flessione del discorso.</span><span class="sxs-lookup"><span data-stu-id="484e8-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="484e8-110">Consente anche di eseguire lo streaming di audio o di un flusso audio TTS dal proprio servizio, offrendo una grande flessibilità per la personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="484e8-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="484e8-111">Esistono due modelli per l'utilizzo delle proprietà Speak da un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="484e8-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="484e8-112">Alla **consegna** : quando viene recapitata una scheda, il client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="484e8-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="484e8-113">**Su richiesta** -per supportare un modello di accessibilità più completo, lo schema supporta un tag Speak per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="484e8-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="484e8-114">Il client può leggere una proprietà Speak per ogni elemento nella scheda.</span><span class="sxs-lookup"><span data-stu-id="484e8-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="484e8-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="484e8-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="484e8-116">Progettazione del contenuto vocale</span><span class="sxs-lookup"><span data-stu-id="484e8-116">Speech content design</span></span>

<span data-ttu-id="484e8-117">Il contenuto progettato per la sintesi vocale è diverso dal contenuto progettato per la visualizzazione visiva.</span><span class="sxs-lookup"><span data-stu-id="484e8-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="484e8-118">Quando si progetta una scheda, si sta progettando un'intera esperienza visiva per presentare le informazioni a un utente in modo che le riaccenda.</span><span class="sxs-lookup"><span data-stu-id="484e8-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="484e8-119">Quando si progetta per la sintesi vocale, è opportuno pensare a come descrivere verbalmente il contenuto in modo che riaccenda l'utente.</span><span class="sxs-lookup"><span data-stu-id="484e8-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
