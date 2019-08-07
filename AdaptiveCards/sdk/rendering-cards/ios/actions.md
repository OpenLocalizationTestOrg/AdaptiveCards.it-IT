---
title: Azioni-iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 3c0a0886ca5b4403292f8d92cccc329325909738
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732998"
---
# <a name="actions---ios"></a><span data-ttu-id="4a9b4-102">Azioni-iOS</span><span class="sxs-lookup"><span data-stu-id="4a9b4-102">Actions - iOS</span></span>

<span data-ttu-id="4a9b4-103">Gli sviluppatori possono ricevere azioni quali SubmitAction e OpenUrl implementando ACRActionDelegate e impostarlo sull'istanza di AdaptiveCard.</span><span class="sxs-lookup"><span data-stu-id="4a9b4-103">Developers can receive actions such SubmitAction and OpenUrl by implementing ACRActionDelegate, and set it to instance of AdaptiveCard.</span></span>

```objective-c
//// delegate implementation
- (void) didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
     if(action.type == ACROpenUrl){
         NSURL *url = [NSURL URLWithString:[action url]];
         SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
         [self presentViewController:svc animated:YES completion:nil];
     }
     else if(action.type == ACRSubmit){
         /// inputs can be examined by method inputs
         NSData * userInputsAsJson = [card inputs];
         NSString *str = [[NSString alloc] initWithData:userInputsAsJson encoding:NSUTF8StringEncoding];
         NSLog(@"user response fetched: %@ with %@", str, [action data]);
     }
}

/// register the delegate with ACRView instance
adaptiveView.acrActionDelegate = self;

/// if using ACRViewController, pass delegate as argument
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];
```