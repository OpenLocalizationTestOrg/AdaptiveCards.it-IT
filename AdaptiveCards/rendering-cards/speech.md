---
title: Gestione del riconoscimento vocale
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ea46a1c2c14a4cd2aded9672d7493561bbebbd16
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732618"
---
# <a name="handling-speech"></a><span data-ttu-id="b099e-102">Gestione del riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="b099e-102">Handling speech</span></span>

<span data-ttu-id="b099e-103">Per supportare le schede adattive vocali, `speak` la proprietà contiene informazioni sulla modalità di lettura di una scheda a un utente.</span><span class="sxs-lookup"><span data-stu-id="b099e-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="b099e-104">Il tag vocale può essere annotato usando il [markup SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="b099e-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="b099e-105">SSML offre la possibilità di controllare la velocità, il tono e l'inflessione del discorso.</span><span class="sxs-lookup"><span data-stu-id="b099e-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="b099e-106">Consente anche di eseguire lo streaming di audio o di un flusso audio TTS dal proprio servizio, offrendo una grande quantità di personalizzazione.</span><span class="sxs-lookup"><span data-stu-id="b099e-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="b099e-107">Esistono due modelli per l'utilizzo delle proprietà Speak da un'applicazione host:</span><span class="sxs-lookup"><span data-stu-id="b099e-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="b099e-108">**alla consegna** : quando viene recapitata una scheda, un client può scegliere di leggere la proprietà Speak per la scheda per descrivere la scheda nel suo complesso.</span><span class="sxs-lookup"><span data-stu-id="b099e-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="b099e-109">**su richiesta** : per supportare un modello di accessibilità più completo, lo schema supporta un tag Speak per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="b099e-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="b099e-110">Questo consente ai client di leggere ogni elemento nei destinatari con i requisiti di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="b099e-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

