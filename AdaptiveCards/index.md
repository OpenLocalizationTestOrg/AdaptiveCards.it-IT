---
title: Cenni preliminari sulle schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d62bae9259a45dd828028e4f866d18fc75924b0c
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733113"
---
# <a name="adaptive-cards-overview"></a><span data-ttu-id="17a36-102">Cenni preliminari sulle schede adattive</span><span class="sxs-lookup"><span data-stu-id="17a36-102">Adaptive Cards Overview</span></span> 

<span data-ttu-id="17a36-103">Le schede adattive sono un formato di scambio di schede aperto che consente agli sviluppatori di scambiare contenuto dell'interfaccia utente in modo comune e coerente.</span><span class="sxs-lookup"><span data-stu-id="17a36-103">Adaptive Cards are an open card exchange format enabling developers to exchange UI content in a common and consistent way.</span></span>

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a><span data-ttu-id="17a36-104">Come funzionano</span><span class="sxs-lookup"><span data-stu-id="17a36-104">How they work</span></span>

<span data-ttu-id="17a36-105">Gli [**autori di schede**](authoring-cards/getting-started.md) descrivono il contenuto come un semplice oggetto JSON.</span><span class="sxs-lookup"><span data-stu-id="17a36-105">[**Card Authors**](authoring-cards/getting-started.md) describe their content as a simple JSON object.</span></span> <span data-ttu-id="17a36-106">Il rendering del contenuto può quindi essere eseguito in modo nativo all'interno di un' [**applicazione host**](rendering-cards/getting-started.md), adattando automaticamente l'aspetto dell'host.</span><span class="sxs-lookup"><span data-stu-id="17a36-106">That content can then be rendered natively inside a [**Host Application**](rendering-cards/getting-started.md), automatically adapting to the look and feel of the Host.</span></span>

<span data-ttu-id="17a36-107">Ad esempio, contoso bot può creare una scheda adattiva tramite bot Framework e, quando viene recapitato a Skype, avrà un aspetto simile a una scheda Skype.</span><span class="sxs-lookup"><span data-stu-id="17a36-107">For example, Contoso Bot can author an Adaptive Card through the Bot Framework, and when delivered to Skype, it will look and feel like a Skype card.</span></span> <span data-ttu-id="17a36-108">Quando lo stesso payload viene inviato a Microsoft teams, avrà un aspetto simile a Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="17a36-108">When that same payload is sent to Microsoft Teams, it will look and feel like Microsoft Teams.</span></span> <span data-ttu-id="17a36-109">Poiché più app host iniziano a supportare le schede adattive, lo stesso payload si illuminerà automaticamente all'interno di queste applicazioni, pur continuando a essere completamente nativo per l'app.</span><span class="sxs-lookup"><span data-stu-id="17a36-109">As more host apps start to support Adaptive Cards, that same payload will automatically light up inside these applications, yet still feel entirely native to the app.</span></span>

<span data-ttu-id="17a36-110">Gli utenti vincono perché tutti hanno familiarità.</span><span class="sxs-lookup"><span data-stu-id="17a36-110">Users win because everything feels familiar.</span></span> <span data-ttu-id="17a36-111">Le app host vincono perché controllano l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="17a36-111">Host apps win because they control the user experience.</span></span> <span data-ttu-id="17a36-112">E gli autori di schede vincono perché i loro contenuti ottengono una copertura più ampia senza alcuna attività aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="17a36-112">And Card Authors win because their content gets broader reach without any additional work.</span></span>

## <a name="goals"></a><span data-ttu-id="17a36-113">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="17a36-113">Goals</span></span> 

<span data-ttu-id="17a36-114">Gli obiettivi per le schede adattive sono:</span><span class="sxs-lookup"><span data-stu-id="17a36-114">The goals for Adaptive Cards are:</span></span>

* <span data-ttu-id="17a36-115">**Portatile** : per qualsiasi app, dispositivo e Framework dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="17a36-115">**Portable** - To any app, device, and UI framework</span></span>
* <span data-ttu-id="17a36-116">**Open** -Libraries e schema sono open source e Shared</span><span class="sxs-lookup"><span data-stu-id="17a36-116">**Open** - Libraries and schema are open source and shared</span></span>
* <span data-ttu-id="17a36-117">**Basso costo** -facile da definire, facile da utilizzare</span><span class="sxs-lookup"><span data-stu-id="17a36-117">**Low cost** - Easy to define, easy to consume</span></span>
* <span data-ttu-id="17a36-118">Mirato espressivo alla lunga coda di contenuti che gli sviluppatori vogliono produrre</span><span class="sxs-lookup"><span data-stu-id="17a36-118">**Expressive** - Targeted at the long tail of content that developers want to produce</span></span>
* <span data-ttu-id="17a36-119">**Puramente** dichiarativo: non è necessario o consentito codice</span><span class="sxs-lookup"><span data-stu-id="17a36-119">**Purely declarative** - No code is needed or allowed</span></span>
* <span data-ttu-id="17a36-120">Con **stile automatico** per le linee guida per l'esperienza utente e il marchio dell'applicazione host</span><span class="sxs-lookup"><span data-stu-id="17a36-120">**Automatically styled** - To the Host application UX and brand guidelines</span></span>

## <a name="for-card-authors"></a><span data-ttu-id="17a36-121">Per gli autori di schede</span><span class="sxs-lookup"><span data-stu-id="17a36-121">For Card Authors</span></span>
<span data-ttu-id="17a36-122">Le schede adattive sono ottime per gli autori di schede:</span><span class="sxs-lookup"><span data-stu-id="17a36-122">Adaptive Cards are great for card authors:</span></span>

* <span data-ttu-id="17a36-123">**Uno schema** : si ottiene un singolo formato, riducendo al minimo il costo della creazione di una scheda e massimizzando il numero di posizioni che è possibile usare.</span><span class="sxs-lookup"><span data-stu-id="17a36-123">**One schema** - You get a single format, minimizing the cost of creating a card and maximizing the number of places it can be used.</span></span>
* <span data-ttu-id="17a36-124">**Espressione più ricca** : il contenuto può essere allineato in modo più accurato con le informazioni desiderate, perché è presente una tavolozza più ricca con cui disegnare.</span><span class="sxs-lookup"><span data-stu-id="17a36-124">**Richer expression** - Your content can more closely align with want you want to say because you have a richer palette to paint with.</span></span>
* <span data-ttu-id="17a36-125">**Ampia copertura** : i contenuti funzioneranno in un set più ampio di applicazioni senza dover apprendere nuovi schemi.</span><span class="sxs-lookup"><span data-stu-id="17a36-125">**Broad reach** - Your content will work across a broader set of applications without you having to learn new schemas.</span></span>
* <span data-ttu-id="17a36-126">**Controlli di input** : la scheda può includere controlli di input per la raccolta di informazioni dall'utente che visualizza la scheda.</span><span class="sxs-lookup"><span data-stu-id="17a36-126">**Input controls** - Your card can include input controls for gathering information from the user that is viewing the card.</span></span>
* <span data-ttu-id="17a36-127">**Strumenti migliori** : un ecosistema di schede aperto significa strumenti migliori condivisi da tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="17a36-127">**Better tooling** - An open card ecosystem means better tooling that is shared by everyone.</span></span>

## <a name="for-experience-owners"></a><span data-ttu-id="17a36-128">Per i proprietari dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="17a36-128">For Experience Owners</span></span>
<span data-ttu-id="17a36-129">Gli sviluppatori di app che desiderano accedere a un ecosistema di contenuto di terze parti apprezzeranno le schede adattive perché:</span><span class="sxs-lookup"><span data-stu-id="17a36-129">If you are an app developer who wants to tap into an ecosystem of third-party content you will love Adaptive Cards because:</span></span>

* <span data-ttu-id="17a36-130">**Esperienza utente coerente** : si garantisce un'esperienza coerente agli utenti, perché si è proprietari dello stile della scheda sottoposta a rendering.</span><span class="sxs-lookup"><span data-stu-id="17a36-130">**Consistent user experience** - You guarantee a consistent experience for your users, because you own the style of the rendered card.</span></span>
* <span data-ttu-id="17a36-131">**Prestazioni native** : si ottengono prestazioni native in quanto destinate direttamente al Framework dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="17a36-131">**Native performance** - You get native performance as it targets your UI framework directly.</span></span>
* <span data-ttu-id="17a36-132">Il contenuto **sicuro** viene fornito in payload sicuri, quindi non è necessario aprire il Framework dell'interfaccia utente per markup non elaborato e scripting.</span><span class="sxs-lookup"><span data-stu-id="17a36-132">**Safe** - Content is delivered in safe payloads so you don't have to open up your UI framework to raw markup and scripting.</span></span>
* <span data-ttu-id="17a36-133">**Facile da implementare** : puoi ottenere le librerie di scaffale per integrarle facilmente in qualsiasi piattaforma supportata</span><span class="sxs-lookup"><span data-stu-id="17a36-133">**Easy to implement** - You get off the shelf libraries to easily integrate on any platform you support</span></span> 
* <span data-ttu-id="17a36-134">**Documentazione gratuita** : è possibile risparmiare tempo perché non è necessario inventare, implementare e documentare uno schema proprietario.</span><span class="sxs-lookup"><span data-stu-id="17a36-134">**Free documentation** - You save time because you don't have to invent, implement, and document a proprietary schema.</span></span>
* <span data-ttu-id="17a36-135">**Strumenti condivisi** : è possibile risparmiare tempo perché non è necessario creare strumenti personalizzati.</span><span class="sxs-lookup"><span data-stu-id="17a36-135">**Shared tooling** - You save time because you don't have to create custom tooling.</span></span>

## <a name="core-design-principles"></a><span data-ttu-id="17a36-136">Principi di progettazione principali</span><span class="sxs-lookup"><span data-stu-id="17a36-136">Core Design Principles</span></span> 

<span data-ttu-id="17a36-137">Le schede adattive sono basate su un set di [principi guida](resources/principles.md) che risultano utili per tenere traccia della progettazione.</span><span class="sxs-lookup"><span data-stu-id="17a36-137">Adaptive Cards are driven by a set of [guiding principles](resources/principles.md) that have been useful for keeping the design on track.</span></span> 

### <a name="semantic-instead-of-pixel-perfect"></a><span data-ttu-id="17a36-138">Semantica anziché pixel-perfetto</span><span class="sxs-lookup"><span data-stu-id="17a36-138">Semantic instead of pixel-perfect</span></span>
<span data-ttu-id="17a36-139">Il più possibile per i valori semantici e i concetti è più mirato rispetto al layout puro in pixel perfetto.</span><span class="sxs-lookup"><span data-stu-id="17a36-139">We have striven as much as possible for semantic values and concepts as opposed to pure pixel-perfect layout.</span></span> <span data-ttu-id="17a36-140">Esempi di espressione semantica vengono visualizzati in colori, dimensioni e in elementi come factt e Imaget.</span><span class="sxs-lookup"><span data-stu-id="17a36-140">Examples of semantic expression show up in colors, sizes, and in elements like FactSet and ImageSet.</span></span> <span data-ttu-id="17a36-141">Che consentono all'applicazione host di prendere decisioni migliori sull'aspetto effettivo.</span><span class="sxs-lookup"><span data-stu-id="17a36-141">These all allow the host application to make better decisions about the actual look and feel.</span></span>

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a><span data-ttu-id="17a36-142">Gli autori di schede possiedono il contenuto, l'app host è proprietaria dell'aspetto</span><span class="sxs-lookup"><span data-stu-id="17a36-142">Card Authors own the content, Host App owns the look and feel</span></span>
<span data-ttu-id="17a36-143">Gli autori delle schede possiedono quello che desiderano, ma l'applicazione che lo Visualizza è proprietario dell'aspetto della scheda nel contesto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="17a36-143">The card authors own what they want to say, but the application displaying it owns the look and feel of the card in the context of their application.</span></span>

### <a name="keep-it-simple-but-expressive"></a><span data-ttu-id="17a36-144">Mantenerlo semplice, ma espressivo</span><span class="sxs-lookup"><span data-stu-id="17a36-144">Keep it simple, but expressive</span></span>
<span data-ttu-id="17a36-145">Si vuole che le schede adattive siano espressive e per utilizzo generico, ma non si vuole creare un Framework dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="17a36-145">We want Adaptive Cards to be expressive and general purpose, but we don't want to build a UI framework.</span></span>  <span data-ttu-id="17a36-146">Lo scopo è quello di creare un livello intermedio che sia "abbastanza espressivo" nello stesso modo in cui Markdown è sufficientemente espressivo per i documenti.</span><span class="sxs-lookup"><span data-stu-id="17a36-146">The goal is to create an intermediate layer which is "expressive enough" in the same way Markdown is expressive enough for documents.</span></span>

<span data-ttu-id="17a36-147">Concentrandosi su un semplice ed espressivo, Markdown ha creato una descrizione semplice e coerente del contenuto del documento.</span><span class="sxs-lookup"><span data-stu-id="17a36-147">By focusing on keeping it simple and expressive, Markdown created an easy and consistent description of document content.</span></span>  <span data-ttu-id="17a36-148">Allo stesso modo, si ritiene che le schede adattive possano creare un semplice strumento espressivo per descrivere il contenuto delle schede.</span><span class="sxs-lookup"><span data-stu-id="17a36-148">In the same way, we believe that Adaptive Cards can create a simple, expressive means of describing card content.</span></span>

### <a name="when-in-doubt-keep-it-out"></a><span data-ttu-id="17a36-149">In caso di dubbi, è opportuno tenerlo fuori</span><span class="sxs-lookup"><span data-stu-id="17a36-149">When in doubt, keep it out</span></span>
<span data-ttu-id="17a36-150">È più facile da aggiungere in un secondo momento, quindi è possibile vivere con un errore.</span><span class="sxs-lookup"><span data-stu-id="17a36-150">It is easier to add later then it is to live with a mistake.</span></span> <span data-ttu-id="17a36-151">Se ci si è rivelato che è opportuno aggiungere qualcosa o meno, è stato scelto di lasciarlo invariato.  È sempre più semplice aggiungere una proprietà rispetto a una legacy che non è supportata.</span><span class="sxs-lookup"><span data-stu-id="17a36-151">If we found ourselves debating whether we should add something or not, we opted to leave it out.  It is always easier to add a property than to live with a legacy we wish we didn't have to support.</span></span>


## <a name="build-2018-session"></a><span data-ttu-id="17a36-152">Compila sessione 2018</span><span class="sxs-lookup"><span data-stu-id="17a36-152">Build 2018 Session</span></span>

<span data-ttu-id="17a36-153">La sessione seguente in Build 2018 presenta le schede adattive in bot, Cortana, Outlook e Windows.</span><span class="sxs-lookup"><span data-stu-id="17a36-153">The following session at Build 2018 showcases Adaptive Cards in Bots, Cortana, Outlook, and Windows.</span></span> 

<iframe src="https://medius.studios.ms/Embed/Video/BRK2401?SFYT=true" width="960" height="540" allowFullScreen frameBorder="0"></iframe>
