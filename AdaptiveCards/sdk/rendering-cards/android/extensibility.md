---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: e565606f4a112d4f1fa08e2989f392f1abf0887f
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68732538"
---
# <a name="extensibility---android"></a><span data-ttu-id="cb38b-102">Estensibilità-Android</span><span class="sxs-lookup"><span data-stu-id="cb38b-102">Extensibility - Android</span></span>

<span data-ttu-id="cb38b-103">Il renderer Android può essere esteso per supportare più scenari, tra cui:</span><span class="sxs-lookup"><span data-stu-id="cb38b-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="cb38b-104">Analisi personalizzata degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="cb38b-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="cb38b-105">Rendering personalizzato degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="cb38b-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="cb38b-106">[Rendering personalizzato delle azioni](#custom-rendering-of-actions) (A partire dalla versione 1.2)</span><span class="sxs-lookup"><span data-stu-id="cb38b-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="cb38b-107">[Caricamento di immagini personalizzate](#custom-image-loading) (A partire dalla versione 1.0.1)</span><span class="sxs-lookup"><span data-stu-id="cb38b-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="cb38b-108">[Caricamento di file multimediali personalizzati](#custom-media-loading) (A partire dalla versione 1.1)</span><span class="sxs-lookup"><span data-stu-id="cb38b-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="cb38b-109">Analisi personalizzata degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="cb38b-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="cb38b-110">È possibile estendere il parser per supportare gli elementi della scheda definiti.</span><span class="sxs-lookup"><span data-stu-id="cb38b-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="cb38b-111">Si immagini, ad esempio, di avere un nuovo tipo di elemento simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="cb38b-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="cb38b-112">Nelle righe seguenti viene illustrato come analizzarlo in un oggetto Cardelement che si estende da BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="cb38b-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

<span data-ttu-id="cb38b-113">Questo è il modo in cui registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento personalizzato:</span><span class="sxs-lookup"><span data-stu-id="cb38b-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="cb38b-114">Viene quindi eseguito il rendering dell'elemento personalizzato</span><span class="sxs-lookup"><span data-stu-id="cb38b-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="cb38b-115">Rendering personalizzato degli elementi della scheda</span><span class="sxs-lookup"><span data-stu-id="cb38b-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="cb38b-116">**Elenco di modifiche di rilievo**</span><span class="sxs-lookup"><span data-stu-id="cb38b-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="cb38b-117">Modifiche di rilievo per v 1.2</span><span class="sxs-lookup"><span data-stu-id="cb38b-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="cb38b-118">Per definire un renderer personalizzato per il tipo, è necessario innanzitutto creare una classe che si estende da ```BaseCardElementRenderer```:</span><span class="sxs-lookup"><span data-stu-id="cb38b-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

<span data-ttu-id="cb38b-119">Si registra quindi questo renderer in questo modo:</span><span class="sxs-lookup"><span data-stu-id="cb38b-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="cb38b-120">Modifiche di rilievo per v 1.2</span><span class="sxs-lookup"><span data-stu-id="cb38b-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="cb38b-121">Il ```render``` metodo è stato modificato in modo ```RenderedAdaptiveCard``` da includere ```ContainerStyle``` il parametro ed è stato modificato per un RenderArgs in cui ContainerStyle è ora contenuto, quindi una classe che estende BaseCardElementRenderer dovrebbe essere simile alla seguente</span><span class="sxs-lookup"><span data-stu-id="cb38b-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="cb38b-122">Analisi personalizzata delle azioni della scheda</span><span class="sxs-lookup"><span data-stu-id="cb38b-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="cb38b-123">Analogamente all'analisi degli elementi della scheda personalizzati nella versione 1.2, è stata introdotta la possibilità di analizzare le azioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="cb38b-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="cb38b-124">Ad esempio, supponiamo di avere un nuovo tipo di azione simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="cb38b-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="cb38b-125">Nelle righe seguenti viene illustrato come analizzarlo in un Actionelement che si estende da ```BaseActionElement```:</span><span class="sxs-lookup"><span data-stu-id="cb38b-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

<span data-ttu-id="cb38b-126">E le righe successive dimostrano come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento azione personalizzata:</span><span class="sxs-lookup"><span data-stu-id="cb38b-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="cb38b-127">Viene quindi eseguito il rendering dell'azione personalizzata</span><span class="sxs-lookup"><span data-stu-id="cb38b-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="cb38b-128">Rendering personalizzato delle azioni</span><span class="sxs-lookup"><span data-stu-id="cb38b-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="cb38b-129">Per definire il renderer dell'azione personalizzata per il tipo, è necessario innanzitutto creare una classe che si estende ```BaseActionElementRenderer```da:</span><span class="sxs-lookup"><span data-stu-id="cb38b-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

<span data-ttu-id="cb38b-130">Si registra quindi questo renderer in questo modo:</span><span class="sxs-lookup"><span data-stu-id="cb38b-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="cb38b-131">Rendering personalizzato delle azioni</span><span class="sxs-lookup"><span data-stu-id="cb38b-131">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="cb38b-132">Le modifiche apportate al rendering personalizzato delle azioni sono pianificate per la versione 1.2 ma non sono ancora state completate</span><span class="sxs-lookup"><span data-stu-id="cb38b-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="cb38b-133">Caricamento di immagini personalizzate</span><span class="sxs-lookup"><span data-stu-id="cb38b-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="cb38b-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="cb38b-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb38b-135">**È possibile registrare un solo IOnlineImageLoader e avere la precedenza rispetto alla modalità predefinita di recupero delle immagini**</span><span class="sxs-lookup"><span data-stu-id="cb38b-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="cb38b-136">Per consentire agli sviluppatori di ottenere immagini che non possono essere scaricate o recuperate da un'origine online o che sono stati richiesti passaggi precedenti prima che potessero essere recuperate, è stato aggiunto IOnlineImageLoader per risolvere questo tipo di situazioni.</span><span class="sxs-lookup"><span data-stu-id="cb38b-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="cb38b-137">Per implementare un OnlineImageLoader è necessario implementare solo il metodo</span><span class="sxs-lookup"><span data-stu-id="cb38b-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="cb38b-138">Di seguito è riportato un esempio di OnlineImageLoader che modifica tutte le immagini per un'immagine cat</span><span class="sxs-lookup"><span data-stu-id="cb38b-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="cb38b-139">Infine, per registrare il caricatore di immagini, è necessario aggiungere questa riga al codice.</span><span class="sxs-lookup"><span data-stu-id="cb38b-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="cb38b-140">IResourceResolver (depreca IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="cb38b-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="cb38b-141">Per la versione 1.2, al renderer Android è stato aggiunto il supporto per ResourceResolvers completi.</span><span class="sxs-lookup"><span data-stu-id="cb38b-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="cb38b-142">L'implementazione di un sistema di risoluzione delle risorse è molto simile a quella di un IOnlineImageLoader, ma la presenza di ResourceResolvers consente agli sviluppatori di aggiungere più modi per recuperare immagini da qualsiasi tipo di origine in una singola scheda. questa operazione viene eseguita collegando ogni ResourceResolver a un prefisso univoco su cui verrà eseguita una query quando si tenta di recuperare un'immagine.</span><span class="sxs-lookup"><span data-stu-id="cb38b-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="cb38b-143">È possibile implementare un ResourceResolver simile a questo</span><span class="sxs-lookup"><span data-stu-id="cb38b-143">You can implement a ResourceResolver similar to this</span></span>

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="cb38b-144">Come indicato in precedenza, è possibile registrare più ResourceResolvers, per registrare un ResourceResolver è possibile eseguire questa operazione</span><span class="sxs-lookup"><span data-stu-id="cb38b-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="cb38b-145">Trasformazione di un IOnlineImageLoader in un IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="cb38b-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="cb38b-146">La trasformazione di un IOnlineImageLoader in un IResourceResolver è un'attività piuttosto semplice, perché i metodi per quest'ultimo sono stati tentati di rimanere così come il IOnlineImageLoader più possibile</span><span class="sxs-lookup"><span data-stu-id="cb38b-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="cb38b-147">Come si può notare, le modifiche più importanti sono:</span><span class="sxs-lookup"><span data-stu-id="cb38b-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="cb38b-148">```loadOnlineImage(String, GenericImageLoaderAsync)```è stato rinominato in```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="cb38b-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="cb38b-149">un overload per ```resolveImageResource(String, GenericImageLoaderAsync)``` è stato aggiunto ```resolveImageResource(String, GenericImageLoaderAsync, int)``` come per supportare scenari in cui è richiesta la larghezza massima</span><span class="sxs-lookup"><span data-stu-id="cb38b-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="cb38b-150">Caricamento di file multimediali personalizzati</span><span class="sxs-lookup"><span data-stu-id="cb38b-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb38b-151">**È ```IOnlineMediaLoader``` necessario```MediaDataSource``` ricordare che è stato aggiunto a livello API 23 o Android M**</span><span class="sxs-lookup"><span data-stu-id="cb38b-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="cb38b-152">Oltre all'inclusione dell'elemento media, è stata anche l'inclusione dell'interfaccia IOnlineMediaLoader che consente agli sviluppatori di eseguire l'override di [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) usato per l'elemento mediaPlayer sottostante.</span><span class="sxs-lookup"><span data-stu-id="cb38b-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="cb38b-153">**(Richiede Android M)**</span><span class="sxs-lookup"><span data-stu-id="cb38b-153">**(Requires android M)**</span></span>

<span data-ttu-id="cb38b-154">La prima cosa da fare è creare una classe che implementi IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="cb38b-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

<span data-ttu-id="cb38b-155">Dopo che questa classe è stata implementata, è possibile registrare la classe OnlineMediaLoader aggiungendo</span><span class="sxs-lookup"><span data-stu-id="cb38b-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```