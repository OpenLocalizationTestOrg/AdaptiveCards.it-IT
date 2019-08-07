---
title: Implementazione di un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732613"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="d454e-102">Specifica del renderer di schede adattive</span><span class="sxs-lookup"><span data-stu-id="d454e-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="d454e-103">Nella specifica seguente viene descritto come implementare un renderer di schede adattivo su qualsiasi piattaforma dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d454e-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="d454e-104">Il contenuto non è ancora terminato.</span><span class="sxs-lookup"><span data-stu-id="d454e-104">This content is not finished yet.</span></span> <span data-ttu-id="d454e-105">Tornare a breve.</span><span class="sxs-lookup"><span data-stu-id="d454e-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="d454e-106">Controllo delle versioni dell'SDK</span><span class="sxs-lookup"><span data-stu-id="d454e-106">SDK Versioning</span></span>

1. <span data-ttu-id="d454e-107">La versione principale e secondaria dell'SDK **deve** corrispondere `schema` alla versione.</span><span class="sxs-lookup"><span data-stu-id="d454e-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="d454e-108">Patch/Build **deve** essere usato per gli aggiornamenti del renderer che non hanno modifiche dello schema.</span><span class="sxs-lookup"><span data-stu-id="d454e-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="d454e-109">Analisi di JSON</span><span class="sxs-lookup"><span data-stu-id="d454e-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="d454e-110">Condizioni di errore</span><span class="sxs-lookup"><span data-stu-id="d454e-110">Error conditions</span></span>
1. <span data-ttu-id="d454e-111">Un parser **deve** verificare che sia contenuto JSON valido</span><span class="sxs-lookup"><span data-stu-id="d454e-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="d454e-112">Un parser **deve** convalidare lo schema (proprietà obbligatorie e così via)</span><span class="sxs-lookup"><span data-stu-id="d454e-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="d454e-113">Gli errori precedenti **devono** essere segnalati all'app host (eccezione o equivalente)</span><span class="sxs-lookup"><span data-stu-id="d454e-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="d454e-114">Tipi sconosciuti</span><span class="sxs-lookup"><span data-stu-id="d454e-114">Unknown types</span></span>
1. <span data-ttu-id="d454e-115">Se vengono rilevati "tipi" sconosciuti, è **necessario eliminarli** dal risultato</span><span class="sxs-lookup"><span data-stu-id="d454e-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="d454e-116">Eventuali modifiche del payload (come sopra) **devono** essere segnalate come avvisi all'app host</span><span class="sxs-lookup"><span data-stu-id="d454e-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="d454e-117">Proprietà sconosciute</span><span class="sxs-lookup"><span data-stu-id="d454e-117">Unknown properties</span></span>
1. <span data-ttu-id="d454e-118">Un parser **deve** includere proprietà **aggiuntive** sugli elementi</span><span class="sxs-lookup"><span data-stu-id="d454e-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="d454e-119">Ulteriori considerazioni</span><span class="sxs-lookup"><span data-stu-id="d454e-119">Additional considerations</span></span>
1. <span data-ttu-id="d454e-120">La `speak` proprietà può contenere il markup SSML e **deve** essere restituita all'app host come specificato</span><span class="sxs-lookup"><span data-stu-id="d454e-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="d454e-121">Analisi della configurazione dell'host</span><span class="sxs-lookup"><span data-stu-id="d454e-121">Parsing Host Config</span></span>
1. <span data-ttu-id="d454e-122">TODO</span><span class="sxs-lookup"><span data-stu-id="d454e-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="d454e-123">Controllo delle versioni</span><span class="sxs-lookup"><span data-stu-id="d454e-123">Versioning</span></span>

1. <span data-ttu-id="d454e-124">Un renderer **deve** implementare una particolare versione dello schema.</span><span class="sxs-lookup"><span data-stu-id="d454e-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="d454e-125">Il `AdaptiveCard` costruttore **deve** fornire alla `version` proprietà un valore predefinito in base alla versione dello schema corrente.</span><span class="sxs-lookup"><span data-stu-id="d454e-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="d454e-126">Se un renderer rileva `version` una proprietà `AdaptiveCard` in maggiore della versione supportata, **deve** invece restituire l'oggetto `fallbackText` .</span><span class="sxs-lookup"><span data-stu-id="d454e-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="d454e-127">Rendering</span><span class="sxs-lookup"><span data-stu-id="d454e-127">Rendering</span></span>

<span data-ttu-id="d454e-128">Un `AdaptiveCard` oggetto è costituito `actions`da un oggetto `body` e da.</span><span class="sxs-lookup"><span data-stu-id="d454e-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="d454e-129">È una raccolta di `CardElement`oggetti che un renderer enumera e esegue il rendering nell'ordine. `body`</span><span class="sxs-lookup"><span data-stu-id="d454e-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="d454e-130">Ogni elemento **deve** estendersi alla larghezza del padre (think `display: block` in HTML).</span><span class="sxs-lookup"><span data-stu-id="d454e-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="d454e-131">Un renderer **deve** ignorare i tipi di elemento sconosciuti e continuare a eseguire il rendering del resto del payload.</span><span class="sxs-lookup"><span data-stu-id="d454e-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="d454e-132">Spaziatura e separatori</span><span class="sxs-lookup"><span data-stu-id="d454e-132">Spacing and Separators</span></span>

1. <span data-ttu-id="d454e-133">La `spacing` proprietà di ogni elemento influisce sulla quantità di spazio tra l'elemento **corrente** e quello **precedente** .</span><span class="sxs-lookup"><span data-stu-id="d454e-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="d454e-134">La spaziatura deve essere applicata **solo** quando esiste effettivamente un elemento che la precede.</span><span class="sxs-lookup"><span data-stu-id="d454e-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="d454e-135">(Ad esempio, non si applica al primo elemento di una matrice)</span><span class="sxs-lookup"><span data-stu-id="d454e-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="d454e-136">Un renderer **deve** cercare la quantità di spazio da usare dalla `hostConfig` spaziatura per il valore enum applicato all'elemento corrente.</span><span class="sxs-lookup"><span data-stu-id="d454e-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="d454e-137">Se l'elemento ha un `separator` `true`valore, sarà **necessario** tracciare una riga visibile tra l'elemento corrente e quello precedente.</span><span class="sxs-lookup"><span data-stu-id="d454e-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="d454e-138">La linea di separazione **deve** essere disegnata `container.style.default.foregroundColor`utilizzando.</span><span class="sxs-lookup"><span data-stu-id="d454e-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="d454e-139">È necessario disegnare un separatore **solo** se l'elemento **non è** il primo nella matrice.</span><span class="sxs-lookup"><span data-stu-id="d454e-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="d454e-140">Colonne</span><span class="sxs-lookup"><span data-stu-id="d454e-140">Columns</span></span>

1. <span data-ttu-id="d454e-141">`Column`Deve essere interpretato da "auto", "Stretch" o da un rapporto ponderato. `width`</span><span class="sxs-lookup"><span data-stu-id="d454e-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="d454e-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d454e-142">TextBlock</span></span>

1. <span data-ttu-id="d454e-143">Un TextBlock **deve** assumere una sola riga, a meno che `wrap` la proprietà `true`non sia.</span><span class="sxs-lookup"><span data-stu-id="d454e-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="d454e-144">Il blocco di testo **deve** tagliare qualsiasi testo in eccesso con i puntini di sospensione (...)</span><span class="sxs-lookup"><span data-stu-id="d454e-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="d454e-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="d454e-145">Markdown</span></span>

1. <span data-ttu-id="d454e-146">Le schede adattive consentono un subset di Markdown e **devono** essere supportate in `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="d454e-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="d454e-147">Vedere i [requisiti Markdown](../authoring-cards/text-features.md) completi</span><span class="sxs-lookup"><span data-stu-id="d454e-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="d454e-148">Funzioni di formattazione</span><span class="sxs-lookup"><span data-stu-id="d454e-148">Formatting functions</span></span>

1. <span data-ttu-id="d454e-149">`TextBlock`consente le [funzioni di formattazione di data/ora](../authoring-cards/text-features.md) che **devono** essere supportate in ogni renderer.</span><span class="sxs-lookup"><span data-stu-id="d454e-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="d454e-150">**Tutti gli errori devono** visualizzare la stringa non elaborata nella scheda.</span><span class="sxs-lookup"><span data-stu-id="d454e-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="d454e-151">Nessun messaggio descrittivo provato.</span><span class="sxs-lookup"><span data-stu-id="d454e-151">No friendly message attempted.</span></span> <span data-ttu-id="d454e-152">(L'obiettivo è quello di rendere lo sviluppatore immediatamente in grado di riconoscere la presenza di un problema)</span><span class="sxs-lookup"><span data-stu-id="d454e-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="d454e-153">TODO: Includi Regex</span><span class="sxs-lookup"><span data-stu-id="d454e-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="d454e-154">Immagini</span><span class="sxs-lookup"><span data-stu-id="d454e-154">Images</span></span>

1. <span data-ttu-id="d454e-155">Un renderer **deve** consentire alle app host di rilevare il momento in cui tutte le immagini http sono state scaricate e la scheda è "completamente sottoposta a rendering"</span><span class="sxs-lookup"><span data-stu-id="d454e-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="d454e-156">Un renderer **deve** controllare il param config `maxImageSize` dell'host durante il download delle immagini http</span><span class="sxs-lookup"><span data-stu-id="d454e-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="d454e-157">Un renderer **deve** supportare `.png` e`.jpeg`</span><span class="sxs-lookup"><span data-stu-id="d454e-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="d454e-158">Un renderer **deve** supportare `.gif` le immagini</span><span class="sxs-lookup"><span data-stu-id="d454e-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="d454e-159">Configurazione host</span><span class="sxs-lookup"><span data-stu-id="d454e-159">Host Config</span></span>

* <span data-ttu-id="d454e-160">TODO: Quali sono le impostazioni predefinite?</span><span class="sxs-lookup"><span data-stu-id="d454e-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="d454e-161">Tutte le condivisioni?</span><span class="sxs-lookup"><span data-stu-id="d454e-161">Should they all share it?</span></span> <span data-ttu-id="d454e-162">È necessario incorporare un file hostConfig. JSON comune nei file binari?</span><span class="sxs-lookup"><span data-stu-id="d454e-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="d454e-163">TODO: Credo che anche HostConfig debba essere sottoposto a controllo delle versioni per l'analisi?</span><span class="sxs-lookup"><span data-stu-id="d454e-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="d454e-164">[`HostConfig`](host-config.md)è un oggetto di configurazione condivisa che specifica il modo in cui un renderer di schede adattivo genera l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d454e-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="d454e-165">Ciò consente di condividere le proprietà indipendenti dalla piattaforma tra i renderer su piattaforme e dispositivi diversi.</span><span class="sxs-lookup"><span data-stu-id="d454e-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="d454e-166">Consente inoltre di creare strumenti che offrono un'idea dell'aspetto che avrebbe la scheda per un determinato ambiente.</span><span class="sxs-lookup"><span data-stu-id="d454e-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="d454e-167">I renderer **devono** esporre un parametro di **Configurazione host** per le app host</span><span class="sxs-lookup"><span data-stu-id="d454e-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="d454e-168">Tutti gli elementi **devono** avere uno stile in base alle rispettive impostazioni di configurazione host</span><span class="sxs-lookup"><span data-stu-id="d454e-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="d454e-169">Stile della piattaforma nativa</span><span class="sxs-lookup"><span data-stu-id="d454e-169">Native platform styling</span></span>

1. <span data-ttu-id="d454e-170">Ogni tipo di elemento **deve** associare uno stile di piattaforma nativo con l'elemento dell'interfaccia utente generato.</span><span class="sxs-lookup"><span data-stu-id="d454e-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="d454e-171">Ad esempio, in HTML è stata aggiunta una classe CSS ai tipi di elemento e in XAML viene assegnato uno stile specifico.</span><span class="sxs-lookup"><span data-stu-id="d454e-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="d454e-172">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="d454e-172">Extensibility</span></span> 

1. <span data-ttu-id="d454e-173">Un renderer **deve** consentire alle app host di eseguire l'override di renderer di elementi predefiniti.</span><span class="sxs-lookup"><span data-stu-id="d454e-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="d454e-174">Ad esempio, sostituire `TextBlock` il rendering con la propria logica.</span><span class="sxs-lookup"><span data-stu-id="d454e-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="d454e-175">Un renderer **deve** consentire alle app host di registrare tipi di elementi personalizzati.</span><span class="sxs-lookup"><span data-stu-id="d454e-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="d454e-176">Ad esempio, aggiungere il supporto per un `Rating` elemento personalizzato</span><span class="sxs-lookup"><span data-stu-id="d454e-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="d454e-177">Un renderer **deve** consentire alle app host di rimuovere il supporto per un elemento predefinito.</span><span class="sxs-lookup"><span data-stu-id="d454e-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="d454e-178">Ad esempio, rimuovere `Action.Submit` se non si vuole che sia supportata.</span><span class="sxs-lookup"><span data-stu-id="d454e-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="d454e-179">Azioni</span><span class="sxs-lookup"><span data-stu-id="d454e-179">Actions</span></span>

1. <span data-ttu-id="d454e-180">Se Hostconfig `supportsInteractivity` è `false`, un renderer **non deve** eseguire il rendering di alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="d454e-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="d454e-181">La `actions` proprietà **deve** essere sottoposta a rendering come pulsanti in un certo tipo di barra delle azioni, in genere nella parte inferiore della scheda.</span><span class="sxs-lookup"><span data-stu-id="d454e-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="d454e-182">Quando si tocca un pulsante, è **necessario** consentire all'app host di gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="d454e-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="d454e-183">L'evento **deve** passare tutte le proprietà associate con l'azione</span><span class="sxs-lookup"><span data-stu-id="d454e-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="d454e-184">L'evento **deve** passare lungo l' `AdaptiveCard` oggetto che è stato eseguito</span><span class="sxs-lookup"><span data-stu-id="d454e-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="d454e-185">Azione</span><span class="sxs-lookup"><span data-stu-id="d454e-185">Action</span></span> | <span data-ttu-id="d454e-186">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d454e-186">Behavior</span></span>
--- | ---
<span data-ttu-id="d454e-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="d454e-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="d454e-188">Aprire un URL esterno per la visualizzazione</span><span class="sxs-lookup"><span data-stu-id="d454e-188">Open an external URL for viewing</span></span>
<span data-ttu-id="d454e-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="d454e-189">**Action.ShowCard**</span></span> | <span data-ttu-id="d454e-190">Richiede che una scheda secondaria venga visualizzata all'utente.</span><span class="sxs-lookup"><span data-stu-id="d454e-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="d454e-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="d454e-191">**Action.Submit**</span></span> | <span data-ttu-id="d454e-192">Chiedere a tutti gli elementi di input di essere raccolti in un oggetto che viene quindi inviato tramite un metodo definito dall'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="d454e-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="d454e-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d454e-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="d454e-194">`Action.OpenUrl`**Deve** aprire un URL usando il meccanismo della piattaforma nativa</span><span class="sxs-lookup"><span data-stu-id="d454e-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="d454e-195">Se questo non è possibile, **deve** generare un evento nell'app host per gestire l'apertura dell'URL.</span><span class="sxs-lookup"><span data-stu-id="d454e-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="d454e-196">Questo evento **deve** consentire all'app host di eseguire l'override del comportamento predefinito.</span><span class="sxs-lookup"><span data-stu-id="d454e-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="d454e-197">Ad esempio, consente di aprire l'URL all'interno della propria app.</span><span class="sxs-lookup"><span data-stu-id="d454e-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="d454e-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d454e-198">Action.ShowCard</span></span>

1. <span data-ttu-id="d454e-199">`Action.ShowCard`**Deve** essere supportato in qualche modo, in base all'impostazione hostConfig.</span><span class="sxs-lookup"><span data-stu-id="d454e-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="d454e-200">Sono disponibili due modalità: inline e popup.</span><span class="sxs-lookup"><span data-stu-id="d454e-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="d454e-201">Le schede inline **devono** impostare la visibilità della scheda automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d454e-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="d454e-202">In modalità popup, un evento **deve** essere generato nell'app host per mostrare la scheda in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="d454e-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="d454e-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d454e-203">Action.Submit</span></span>

<span data-ttu-id="d454e-204">L'azione di invio si comporta come un modulo HTML submit, ad eccezione del fatto che, nel caso in cui il codice HTML attivi un post HTTP, le schede adattive lo lasciano a ogni app host per determinare il significato "Submit".</span><span class="sxs-lookup"><span data-stu-id="d454e-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="d454e-205">Quando **deve** generare un evento, l'utente tocca l'azione richiamata.</span><span class="sxs-lookup"><span data-stu-id="d454e-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="d454e-206">La `data` proprietà **deve** essere inclusa nel payload di callback.</span><span class="sxs-lookup"><span data-stu-id="d454e-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="d454e-207">Per `Action.Submit`, un renderer **deve** raccogliere tutti gli input sulla scheda e recuperare i relativi valori.</span><span class="sxs-lookup"><span data-stu-id="d454e-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="d454e-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="d454e-208">selectAction</span></span>

1. <span data-ttu-id="d454e-209">`supportedInteractivity` Se la `false` configurazione host è quindi, non è necessario eseguire il rendering come destinazione tocco. `selectAction`</span><span class="sxs-lookup"><span data-stu-id="d454e-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="d454e-210">`Image`, `ColumnSet`e `Column` offrono una`selectAction` proprietà, che **deve** essere eseguita quando viene richiamata dall'utente, ad esempio, toccando l'elemento.</span><span class="sxs-lookup"><span data-stu-id="d454e-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="d454e-211">Input</span><span class="sxs-lookup"><span data-stu-id="d454e-211">Inputs</span></span>

1. <span data-ttu-id="d454e-212">Se Hostconfig `supportsInteractivity` è `false` un renderer **non deve** eseguire il rendering degli input.</span><span class="sxs-lookup"><span data-stu-id="d454e-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="d454e-213">Gli input **devono** essere sottoposte a rendering con la massima fedeltà possibile.</span><span class="sxs-lookup"><span data-stu-id="d454e-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="d454e-214">Un oggetto `Input.Date` , ad esempio, offrirebbe idealmente una selezione data a un utente, ma se questo non è possibile nello stack dell'interfaccia utente, il renderer **deve** eseguire il fallback per il rendering di una casella di testo standard.</span><span class="sxs-lookup"><span data-stu-id="d454e-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="d454e-215">Un renderer **dovrebbe** visualizzare `placeholderText` , se possibile</span><span class="sxs-lookup"><span data-stu-id="d454e-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="d454e-216">**Non** è necessario che un renderer implementi la convalida dell'input.</span><span class="sxs-lookup"><span data-stu-id="d454e-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="d454e-217">Gli utenti di schede adattive devono pianificare la convalida dei dati ricevuti alla fine.</span><span class="sxs-lookup"><span data-stu-id="d454e-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="d454e-218">Il valore di input **deve** essere preceduto da un carattere di escape</span><span class="sxs-lookup"><span data-stu-id="d454e-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="d454e-219">L'oggetto **deve** essere restituito all'app host nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d454e-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="d454e-220">Non viene eseguita alcuna promessa di convalida dell'input nelle schede adattive, pertanto spetta all'entità ricevente analizzare correttamente la risposta.</span><span class="sxs-lookup"><span data-stu-id="d454e-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="d454e-221">Ad esempio, un input. Number può restituire "Hello" ed è necessario prepararlo.</span><span class="sxs-lookup"><span data-stu-id="d454e-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="d454e-222">Eventi</span><span class="sxs-lookup"><span data-stu-id="d454e-222">Events</span></span>

1. <span data-ttu-id="d454e-223">Un renderer **deve** generare un evento quando la visibilità di un elemento è cambiata, consentendo all'app host di scorrere la scheda in posizione.</span><span class="sxs-lookup"><span data-stu-id="d454e-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
