---
title: Stile nativo-UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: 565c61535adc5b316cb8b1f3ad77e511012e7612
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732543"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="30354-102">Stile nativo-UWP</span><span class="sxs-lookup"><span data-stu-id="30354-102">Native styling - UWP</span></span>

<span data-ttu-id="30354-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="30354-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="30354-104">UWP semplifica questa operazione consentendo di passare un oggetto ResourceDictionary per lo stile, il comportamento, le animazioni e così via.</span><span class="sxs-lookup"><span data-stu-id="30354-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="30354-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="30354-105">Element</span></span> | <span data-ttu-id="30354-106">Nomi di stile</span><span class="sxs-lookup"><span data-stu-id="30354-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="30354-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="30354-107">AdaptiveCard</span></span> | <span data-ttu-id="30354-108">Adaptive. Card</span><span class="sxs-lookup"><span data-stu-id="30354-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="30354-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="30354-109">Action.OpenUrl</span></span>  | <span data-ttu-id="30354-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="30354-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="30354-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="30354-111">Action.ShowCard</span></span> | <span data-ttu-id="30354-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="30354-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="30354-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="30354-113">Action.Submit</span></span>  | <span data-ttu-id="30354-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="30354-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="30354-115">Colonna</span><span class="sxs-lookup"><span data-stu-id="30354-115">Column</span></span> | <span data-ttu-id="30354-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="30354-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="30354-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="30354-117">ColumnSet</span></span> | <span data-ttu-id="30354-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="30354-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="30354-119">Contenitore</span><span class="sxs-lookup"><span data-stu-id="30354-119">Container</span></span> | <span data-ttu-id="30354-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="30354-120">Adaptive.Container</span></span>|
| <span data-ttu-id="30354-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="30354-121">Input.ChoiceSet</span></span> | <span data-ttu-id="30354-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="30354-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="30354-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="30354-123">Input.Date</span></span> | <span data-ttu-id="30354-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="30354-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="30354-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="30354-125">Input.Number</span></span> | <span data-ttu-id="30354-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="30354-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="30354-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="30354-127">Input.Text</span></span> | <span data-ttu-id="30354-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="30354-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="30354-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="30354-129">Input.Time</span></span> | <span data-ttu-id="30354-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="30354-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="30354-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="30354-131">Input.Toggle</span></span>| <span data-ttu-id="30354-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="30354-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="30354-133">Image</span><span class="sxs-lookup"><span data-stu-id="30354-133">Image</span></span>  | <span data-ttu-id="30354-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="30354-134">Adaptive.Image</span></span> |
| <span data-ttu-id="30354-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="30354-135">ImageSet</span></span>  | <span data-ttu-id="30354-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="30354-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="30354-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="30354-137">FactSet</span></span> | <span data-ttu-id="30354-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="30354-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="30354-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="30354-139">TextBlock</span></span>  | <span data-ttu-id="30354-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="30354-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="30354-141">Questo dizionario risorse XAML di esempio che imposta lo sfondo di tutti i TextBlock su Aqua.</span><span class="sxs-lookup"><span data-stu-id="30354-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="30354-142">È probabile che si desideri qualcosa di più avanzato😁</span><span class="sxs-lookup"><span data-stu-id="30354-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;
```