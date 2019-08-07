---
title: Stile nativo-.NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732838"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="b2e8e-102">Stile nativo-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="b2e8e-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="b2e8e-103">Sebbene la configurazione host consentirà di ottenere la maggior parte delle piattaforme in ogni piattaforma, è probabile che sarà necessario eseguire alcuni stili nativi su ogni piattaforma.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="b2e8e-104">HTML semplifica questa operazione aggiungendo classi CSS a ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="b2e8e-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2e8e-105">Element</span></span> | <span data-ttu-id="b2e8e-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="b2e8e-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="b2e8e-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="b2e8e-107">AdaptiveCard</span></span> | <span data-ttu-id="b2e8e-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="b2e8e-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="b2e8e-109">Tutte le azioni</span><span class="sxs-lookup"><span data-stu-id="b2e8e-109">All Actions</span></span> | <span data-ttu-id="b2e8e-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="b2e8e-110">ac-pushButton</span></span> | 
| <span data-ttu-id="b2e8e-111">Seleziona azioni</span><span class="sxs-lookup"><span data-stu-id="b2e8e-111">Select Actions</span></span> | <span data-ttu-id="b2e8e-112">AC-selezionabile</span><span class="sxs-lookup"><span data-stu-id="b2e8e-112">ac-selectable</span></span> |
| <span data-ttu-id="b2e8e-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="b2e8e-113">Action.OpenUrl</span></span>  | <span data-ttu-id="b2e8e-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="b2e8e-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="b2e8e-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="b2e8e-115">Action.ShowCard</span></span> | <span data-ttu-id="b2e8e-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="b2e8e-116">ac-action-showCard</span></span> |
| <span data-ttu-id="b2e8e-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="b2e8e-117">Action.Submit</span></span>  | <span data-ttu-id="b2e8e-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="b2e8e-118">ac-action-submit</span></span>  |
| <span data-ttu-id="b2e8e-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="b2e8e-119">ActionSet</span></span> | <span data-ttu-id="b2e8e-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="b2e8e-120">ac-actionset</span></span> |
| <span data-ttu-id="b2e8e-121">Colonna</span><span class="sxs-lookup"><span data-stu-id="b2e8e-121">Column</span></span> | <span data-ttu-id="b2e8e-122">colonna AC</span><span class="sxs-lookup"><span data-stu-id="b2e8e-122">ac-column</span></span> |
| <span data-ttu-id="b2e8e-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="b2e8e-123">ColumnSet</span></span> | <span data-ttu-id="b2e8e-124">AC-columnstore</span><span class="sxs-lookup"><span data-stu-id="b2e8e-124">ac-columnset</span></span> |
| <span data-ttu-id="b2e8e-125">Contenitore</span><span class="sxs-lookup"><span data-stu-id="b2e8e-125">Container</span></span> | <span data-ttu-id="b2e8e-126">contenitore AC</span><span class="sxs-lookup"><span data-stu-id="b2e8e-126">ac-container</span></span> |
| <span data-ttu-id="b2e8e-127">Tutti gli input</span><span class="sxs-lookup"><span data-stu-id="b2e8e-127">All Inputs</span></span> | <span data-ttu-id="b2e8e-128">ac-input</span><span class="sxs-lookup"><span data-stu-id="b2e8e-128">ac-input</span></span> |
| <span data-ttu-id="b2e8e-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="b2e8e-129">Input.ChoiceSet</span></span> | <span data-ttu-id="b2e8e-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="b2e8e-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="b2e8e-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="b2e8e-131">Input.Date</span></span> | <span data-ttu-id="b2e8e-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="b2e8e-132">ac-dateInput</span></span> |
| <span data-ttu-id="b2e8e-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="b2e8e-133">Input.Number</span></span> | <span data-ttu-id="b2e8e-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="b2e8e-134">ac-numberInput</span></span> |
| <span data-ttu-id="b2e8e-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="b2e8e-135">Input.Text</span></span> | <span data-ttu-id="b2e8e-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="b2e8e-136">ac-textInput</span></span> |
| <span data-ttu-id="b2e8e-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="b2e8e-137">Input.Time</span></span> | <span data-ttu-id="b2e8e-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="b2e8e-138">ac-timeInput</span></span> |
| <span data-ttu-id="b2e8e-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="b2e8e-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="b2e8e-140">Image</span><span class="sxs-lookup"><span data-stu-id="b2e8e-140">Image</span></span>  | <span data-ttu-id="b2e8e-141">AC-image</span><span class="sxs-lookup"><span data-stu-id="b2e8e-141">ac-image</span></span> |
| <span data-ttu-id="b2e8e-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="b2e8e-142">ImageSet</span></span>  | <span data-ttu-id="b2e8e-143">AC-imaget</span><span class="sxs-lookup"><span data-stu-id="b2e8e-143">ac-imageset</span></span> |
| <span data-ttu-id="b2e8e-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="b2e8e-144">FactSet</span></span> | <span data-ttu-id="b2e8e-145">ac-factset</span><span class="sxs-lookup"><span data-stu-id="b2e8e-145">ac-factset</span></span> |
| <span data-ttu-id="b2e8e-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="b2e8e-146">TextBlock</span></span>  | <span data-ttu-id="b2e8e-147">ac-textblock</span><span class="sxs-lookup"><span data-stu-id="b2e8e-147">ac-textblock</span></span> |