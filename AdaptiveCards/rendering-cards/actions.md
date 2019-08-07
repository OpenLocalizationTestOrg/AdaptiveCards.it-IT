---
title: Azioni
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733108"
---
# <a name="actions"></a><span data-ttu-id="8e4d7-102">Azioni</span><span class="sxs-lookup"><span data-stu-id="8e4d7-102">Actions</span></span>

<span data-ttu-id="8e4d7-103">Per impostazione predefinita, le azioni verranno sottoposte a rendering come pulsanti sulla scheda, ma spetta all'app fare in modo che si comportino come previsto.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="8e4d7-104">Ogni SDK è equivalente a un `OnAction` evento che è necessario gestire.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="8e4d7-105">**Action. OpenURL** : apre l'oggetto `url`specificato.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="8e4d7-106">**Action. Submit** : consente di portare il risultato dell'invio e di inviarlo all'origine.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="8e4d7-107">Il modo in cui viene inviato all'origine della scheda è interamente all'utente.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="8e4d7-108">**Action. ShowCard** : richiama una finestra di dialogo ed esegue il rendering della sottoscheda in tale finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="8e4d7-109">Si noti che è necessario gestire questa impostazione solo `ShowCardActionMode` se è impostato `popup`su.</span><span class="sxs-lookup"><span data-stu-id="8e4d7-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>