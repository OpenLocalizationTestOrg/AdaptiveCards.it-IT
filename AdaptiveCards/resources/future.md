---
title: Roadmap per schede adattive
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733093"
---
# <a name="future-work"></a><span data-ttu-id="530b1-102">Lavoro futuro</span><span class="sxs-lookup"><span data-stu-id="530b1-102">Future work</span></span>

<span data-ttu-id="530b1-103">Anche se abbiamo realizzato un ottimo progresso nella definizione di schede adattive, c'è ancora molto lavoro da fare.</span><span class="sxs-lookup"><span data-stu-id="530b1-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="530b1-104">Ci auguriamo che attraverso le community di sviluppatori attive come botness e partner eccezionali, ad esempio slack e Kik, possiamo creare un grande ecosistema di schede multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="530b1-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="530b1-105">Guida di orientamento</span><span class="sxs-lookup"><span data-stu-id="530b1-105">Roadmap</span></span>

<span data-ttu-id="530b1-106">Qui è possibile vedere la [Roadmap corrente (non finale)](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="530b1-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="530b1-107">Si noti che qualsiasi elemento qui è soggetto a modifiche e non è una garanzia di spedizione.</span><span class="sxs-lookup"><span data-stu-id="530b1-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="530b1-108">Idee future</span><span class="sxs-lookup"><span data-stu-id="530b1-108">Future ideas</span></span>

<span data-ttu-id="530b1-109">Di seguito sono riportate alcune idee future, che sono semplicemente nella fase Brainstorm.</span><span class="sxs-lookup"><span data-stu-id="530b1-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="530b1-110">Se si è interessati a una di queste informazioni, inviare un commento.</span><span class="sxs-lookup"><span data-stu-id="530b1-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="530b1-111">Ottime schede per i dati</span><span class="sxs-lookup"><span data-stu-id="530b1-111">Great looking Cards from Data</span></span>

<span data-ttu-id="530b1-112">Sappiamo che molti autori di schede dispongono già di dati ben definiti dietro le proprie carte.</span><span class="sxs-lookup"><span data-stu-id="530b1-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="530b1-113">Il piano prevede l'esplorazione di un modello di modello che consenta la generazione di schede (lato server o lato client) in base ai dati e a un repository di modelli ben definiti e personalizzabili.</span><span class="sxs-lookup"><span data-stu-id="530b1-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="530b1-114">Rendi le schede reattive</span><span class="sxs-lookup"><span data-stu-id="530b1-114">Make cards responsive</span></span>

<span data-ttu-id="530b1-115">I layout delle schede devono essere reattivi nello spazio disponibile.</span><span class="sxs-lookup"><span data-stu-id="530b1-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="530b1-116">Le schede adattive sono adattabili a dispositivi diversi, stili di UX e Framework dell'interfaccia utente, ma non sono ancora stati riattivati.</span><span class="sxs-lookup"><span data-stu-id="530b1-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="530b1-117">Per gli elementi è necessario definire proprietà aggiuntive che consentano ai produttori di schede di fornire gli hint necessari alle librerie di rendering, in modo che possano modificare il layout in modo intelligente in modo da mantenere lo scopo della scheda.</span><span class="sxs-lookup"><span data-stu-id="530b1-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="530b1-118">Esplorazione reattiva</span><span class="sxs-lookup"><span data-stu-id="530b1-118">Responsive exploration</span></span>

* <span data-ttu-id="530b1-119">Aggiungere una proprietà di **importanza** che annotare l'importanza del contenuto.</span><span class="sxs-lookup"><span data-stu-id="530b1-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="530b1-120">È possibile eliminare contenuto meno importante per adattarlo allo spazio disponibile</span><span class="sxs-lookup"><span data-stu-id="530b1-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="530b1-121">Aggiungere **vincoli** e proprietà dei **criteri** che descrivono come reagire quando non è possibile soddisfare i vincoli.</span><span class="sxs-lookup"><span data-stu-id="530b1-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="530b1-122">Nascondi contenuto o Comprimi contenuto a dimensioni inferiori.</span><span class="sxs-lookup"><span data-stu-id="530b1-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="530b1-123">Aggiungere una soglia che, quando superata, viene `columnSet` modificata in carosello di colonne.</span><span class="sxs-lookup"><span data-stu-id="530b1-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="530b1-124">Nuovi tipi di elemento</span><span class="sxs-lookup"><span data-stu-id="530b1-124">New element types</span></span>

* <span data-ttu-id="530b1-125">Mappe?</span><span class="sxs-lookup"><span data-stu-id="530b1-125">Maps?</span></span> <span data-ttu-id="530b1-126">-incorporare una mappa in una scheda con interattività o fallback a bitmap</span><span class="sxs-lookup"><span data-stu-id="530b1-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="530b1-127">*Quali elementi si desiderano o sono necessari*?</span><span class="sxs-lookup"><span data-stu-id="530b1-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="530b1-128">Nuove librerie di rendering</span><span class="sxs-lookup"><span data-stu-id="530b1-128">New rendering libraries</span></span>

* <span data-ttu-id="530b1-129">React?</span><span class="sxs-lookup"><span data-stu-id="530b1-129">React?</span></span>
* <span data-ttu-id="530b1-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="530b1-130">Xamarin?</span></span>
* <span data-ttu-id="530b1-131">*Quali sono i Framework desiderati?*</span><span class="sxs-lookup"><span data-stu-id="530b1-131">*What frameworks do you want?*</span></span>
