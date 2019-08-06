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
# <a name="extensibility---android"></a>Estensibilità-Android

Il renderer Android può essere esteso per supportare più scenari, tra cui:
* [Analisi personalizzata degli elementi della scheda](#custom-parsing-of-card-elements)
* [Rendering personalizzato degli elementi della scheda](#custom-rendering-of-card-elements)
* [Rendering personalizzato delle azioni](#custom-rendering-of-actions) (A partire dalla versione 1.2)
* [Caricamento di immagini personalizzate](#custom-image-loading) (A partire dalla versione 1.0.1)
* [Caricamento di file multimediali personalizzati](#custom-media-loading) (A partire dalla versione 1.1)

## <a name="custom-parsing-of-card-elements"></a>Analisi personalizzata degli elementi della scheda

È possibile estendere il parser per supportare gli elementi della scheda definiti. Si immagini, ad esempio, di avere un nuovo tipo di elemento simile al seguente:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Nelle righe seguenti viene illustrato come analizzarlo in un oggetto Cardelement che si estende da BaseCardElement:
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

Questo è il modo in cui registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento personalizzato:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Viene quindi eseguito il rendering dell'elemento personalizzato

## <a name="custom-rendering-of-card-elements"></a>Rendering personalizzato degli elementi della scheda

> [!IMPORTANT]
>
> **Elenco di modifiche di rilievo**
>
> [Modifiche di rilievo per v 1.2](#breaking-changes-for-v12)

Per definire un renderer personalizzato per il tipo, è necessario innanzitutto creare una classe che si estende da ```BaseCardElementRenderer```:
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

Si registra quindi questo renderer in questo modo:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>Modifiche di rilievo per v 1.2

Il ```render``` metodo è stato modificato in modo ```RenderedAdaptiveCard``` da includere ```ContainerStyle``` il parametro ed è stato modificato per un RenderArgs in cui ContainerStyle è ora contenuto, quindi una classe che estende BaseCardElementRenderer dovrebbe essere simile alla seguente

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>Analisi personalizzata delle azioni della scheda

Analogamente all'analisi degli elementi della scheda personalizzati nella versione 1.2, è stata introdotta la possibilità di analizzare le azioni personalizzate. Ad esempio, supponiamo di avere un nuovo tipo di azione simile al seguente:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

Nelle righe seguenti viene illustrato come analizzarlo in un Actionelement che si estende da ```BaseActionElement```:
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

E le righe successive dimostrano come registrare il parser e ottenere un oggetto AdaptiveCard che contiene l'elemento azione personalizzata:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

Viene quindi eseguito il rendering dell'azione personalizzata

## <a name="custom-rendering-of-actions"></a>Rendering personalizzato delle azioni

Per definire il renderer dell'azione personalizzata per il tipo, è necessario innanzitutto creare una classe che si estende ```BaseActionElementRenderer```da:
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

Si registra quindi questo renderer in questo modo:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>Rendering personalizzato delle azioni

[!IMPORTANT]
> Le modifiche apportate al rendering personalizzato delle azioni sono pianificate per la versione 1.2 ma non sono ancora state completate

## <a name="custom-image-loading"></a>Caricamento di immagini personalizzate

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **È possibile registrare un solo IOnlineImageLoader e avere la precedenza rispetto alla modalità predefinita di recupero delle immagini**

Per consentire agli sviluppatori di ottenere immagini che non possono essere scaricate o recuperate da un'origine online o che sono stati richiesti passaggi precedenti prima che potessero essere recuperate, è stato aggiunto IOnlineImageLoader per risolvere questo tipo di situazioni. Per implementare un OnlineImageLoader è necessario implementare solo il metodo 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Di seguito è riportato un esempio di OnlineImageLoader che modifica tutte le immagini per un'immagine cat

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

Infine, per registrare il caricatore di immagini, è necessario aggiungere questa riga al codice.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (depreca IOnlineImageLoader)

Per la versione 1.2, al renderer Android è stato aggiunto il supporto per ResourceResolvers completi. L'implementazione di un sistema di risoluzione delle risorse è molto simile a quella di un IOnlineImageLoader, ma la presenza di ResourceResolvers consente agli sviluppatori di aggiungere più modi per recuperare immagini da qualsiasi tipo di origine in una singola scheda. questa operazione viene eseguita collegando ogni ResourceResolver a un prefisso univoco su cui verrà eseguita una query quando si tenta di recuperare un'immagine. 

È possibile implementare un ResourceResolver simile a questo

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

Come indicato in precedenza, è possibile registrare più ResourceResolvers, per registrare un ResourceResolver è possibile eseguire questa operazione

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Trasformazione di un IOnlineImageLoader in un IResourceResolver 

La trasformazione di un IOnlineImageLoader in un IResourceResolver è un'attività piuttosto semplice, perché i metodi per quest'ultimo sono stati tentati di rimanere così come il IOnlineImageLoader più possibile

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Come si può notare, le modifiche più importanti sono:

* ```loadOnlineImage(String, GenericImageLoaderAsync)```è stato rinominato in```resolveImageResource(String, GenericImageLoaderAsync)```
* un overload per ```resolveImageResource(String, GenericImageLoaderAsync)``` è stato aggiunto ```resolveImageResource(String, GenericImageLoaderAsync, int)``` come per supportare scenari in cui è richiesta la larghezza massima

## <a name="custom-media-loading"></a>Caricamento di file multimediali personalizzati

> [!IMPORTANT]
> **È ```IOnlineMediaLoader``` necessario```MediaDataSource``` ricordare che è stato aggiunto a livello API 23 o Android M**

Oltre all'inclusione dell'elemento media, è stata anche l'inclusione dell'interfaccia IOnlineMediaLoader che consente agli sviluppatori di eseguire l'override di [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) usato per l'elemento mediaPlayer sottostante. **(Richiede Android M)**

La prima cosa da fare è creare una classe che implementi IOnlineImageLoader

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

Dopo che questa classe è stata implementata, è possibile registrare la classe OnlineMediaLoader aggiungendo 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
