---
title: Parte 1. Introduzione a XAML
description: In un'applicazione di xamarin. Forms, XAML viene usato principalmente per definire il contenuto di una pagina e funziona insieme a un file code-behind visual.
ms.prod: xamarin
ms.assetid: 9073FA0E-BD5A-4492-8A93-54C466F6EDB9
ms.technology: xamarin-forms
author: charlespetzold
ms.author: chape
ms.date: 05/10/2018
ms.openlocfilehash: 5883564841a4ef0e19518dd3b12ee00fe35ed778
ms.sourcegitcommit: b0a1c3969ab2a7b7fe961f4f470d1aa57b1ff2c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049727"
---
# <a name="part-1-getting-started-with-xaml"></a>Parte 1. Introduzione a XAML

_In un'applicazione di xamarin. Forms, XAML viene usato principalmente per definire il contenuto di una pagina e funziona insieme a un file code-behind c# visual._

Il file code-behind fornisce supporto di codice per il markup. Insieme, questi due file contribuiscono a una nuova definizione di classe che include visualizzazioni figlio e l'inizializzazione della proprietà. All'interno del file XAML, classi e proprietà viene fatto riferimento con elementi e attributi XML, e vengono stabiliti i collegamenti tra il markup e il codice.

## <a name="creating-the-solution"></a>Creazione della soluzione

Per iniziare la modifica del primo file XAML, utilizzare Visual Studio o Visual Studio per Mac per creare una nuova soluzione xamarin. Forms. (Selezionare la scheda seguito corrispondenti all'ambiente).

# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

In Windows, utilizzare Visual Studio per selezionare **File > Nuovo > progetto** dal menu. Nel **nuovo progetto** finestra di dialogo, seleziona **Visual c# > multipiattaforma** a sinistra, quindi **Mobile App (xamarin. Forms)** dall'elenco al centro. 

![](get-started-with-xaml-images/win/newprojectdialog.w157.png "Finestra di dialogo Nuovo progetto")

Selezionare un percorso per la soluzione, assegnargli un nome di **XamlSamples** (o secondo le proprie preferenze) e premere **OK**.

Nella schermata successiva, selezionare il **applicazione vuota** modello e il **.NET Standard** strategia di condivisione del codice:

![](get-started-with-xaml-images/win/newcrossplatformapp.png "Finestra di dialogo Nuova App")

Press **OK**. 

Vengono creati quattro progetti nella soluzione: il **XamlSamples** libreria .NET Standard **XamlSamples.Android**, **XamlSamples.iOS**e la piattaforma Windows universale soluzione **XamlSamples.UWP**.

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio per Mac](#tab/vsmac)

In Visual Studio per Mac, selezionare **File > nuova soluzione** dal menu. Nel **nuovo progetto** finestra di dialogo Seleziona **multipiattaforma > App** a sinistra, e **App form vuoto** (*non* **form App** ) dall'elenco di modelli:

![](get-started-with-xaml-images/mac/newprojectdialog1.png "Finestra di dialogo Nuovo progetto 1")

Premere **Avanti**.

Nella finestra di dialogo successiva, assegnare al progetto un nome di **XamlSamples** (o secondo le proprie preferenze). Assicurarsi che il **utilizzare .NET Standard** pulsante di opzione selezionato:

![](get-started-with-xaml-images/mac/newprojectdialog2.png "Finestra di dialogo Nuovo progetto 2")

Premere **Avanti**. 

Nella finestra di dialogo seguente, è possibile selezionare un percorso per il progetto:

![](get-started-with-xaml-images/mac/newprojectdialog3.png "Finestra di dialogo Nuovo progetto 3")

Premere **creare**

Vengono creati tre progetti nella soluzione: il **XamlSamples** libreria .NET Standard **XamlSamples.Android**, e **XamlSamples.iOS**. 

-----

Dopo aver creato il **XamlSamples** soluzione, è consigliabile testare l'ambiente di sviluppo selezionando i vari progetti di piattaforma come progetto di avvio della soluzione e la compilazione e distribuzione dell'applicazione semplice creato da il modello di progetto su emulatori phone o dispositivi.

A meno che non è necessario scrivere codice specifico della piattaforma, condiviso **XamlSamples** progetto di libreria .NET Standard è in cui si prevede di passare praticamente tutto il tempo di programmazione. Questi articoli non verranno più all'esterno di tale progetto.

### <a name="anatomy-of-a-xaml-file"></a>Anatomia di un File XAML

All'interno di **XamlSamples** libreria .NET Standard è una coppia di file con i nomi seguenti:

- **App**, il file XAML; e
- **App.Xaml.cs**, c# *codice* file associato al file XAML.

È necessario fare clic sulla freccia accanto a **app** per visualizzare il file code-behind. 

Entrambi **app** e **App.xaml.cs** contribuiscono a una classe denominata `App` che deriva da `Application`. La maggior parte delle altre classi con i file XAML contribuiscono a una classe che deriva da `ContentPage`; tali file usano il linguaggio XAML per definire il contenuto di un'intera pagina visual. Questo vale per altri due file di **XamlSamples** progetto:

- **MainPage. XAML**, il file XAML; e
- **MainPage.xaml.cs**, il file code-behind c#.

Il **MainPage. XAML** file avrà un aspetto simile al seguente (anche se la formattazione potrebbero essere leggermente diversa):

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:XamlSamples"
             x:Class="XamlSamples.MainPage">

    <StackLayout>
        <!-- Place new controls here -->
        <Label Text="Welcome to Xamarin Forms!" 
               VerticalOptions="Center" 
               HorizontalOptions="Center" />
    </StackLayout>

</ContentPage>
```

Spazio dei nomi XML due ( `xmlns`) dichiarazioni si riferiscono a URI, il primo apparentemente sul sito web di Xamarin e il secondo su Microsoft. Non è necessario creare anche che tali punto URI per il controllo. Non è presente. Sono semplicemente gli URI di proprietà di Xamarin e Microsoft, e fondamentalmente funzionano come identificatori di versione.

La prima dichiarazione dello spazio dei nomi XML significa che tag definiti all'interno del file XAML senza il prefisso fanno riferimento alle classi in xamarin. Forms, ad esempio `ContentPage`. La seconda dichiarazione dello spazio dei nomi definisce un prefisso `x`. Questa opzione viene utilizzata per diversi elementi e attributi intrinseci di XAML stesso e che sono supportati da altre implementazioni di XAML. Tuttavia, questi elementi e attributi sono leggermente diversi a seconda dell'anno incorporato nell'URI. Xamarin. Forms supporta la specifica di XAML 2009, ma non tutte.

Il `local` dichiarazione dello spazio dei nomi consente di accedere ad altre classi dal progetto di libreria .NET Standard.

Alla fine del primo tag, il `x` prefisso viene utilizzato per un attributo denominato `Class`. Poiché l'utilizzo di questo `x` prefisso è praticamente universale per lo spazio dei nomi XAML, gli attributi XAML, ad esempio `Class` sono quasi sempre detti `x:Class`.

Il `x:Class` attributo specifica un nome completo della classe .NET: il `MainPage` classe il `XamlSamples` dello spazio dei nomi. Ciò significa che il file XAML definisce una nuova classe denominata `MainPage` nel `XamlSamples` dello spazio dei nomi che deriva da `ContentPage`: il tag in cui il `x:Class` viene visualizzato l'attributo.

Il `x:Class` attributo può essere visualizzato solo nell'elemento radice di un file XAML per definire una classe derivata di c#. Questa è la classe solo nuova definita nel file XAML. Tutte le informazioni presenti nel file XAML è invece sufficiente creare un'istanza da classi esistenti e inizializzata.

Il **MainPage.xaml.cs** file avrà un aspetto simile al seguente (a parte inutilizzata `using` direttive):

```csharp
using Xamarin.Forms;

namespace XamlSamples
{
    public partial class MainPage : ContentPage
    {
        public MainPage()
        {
            InitializeComponent();
        }
    }
}
```

Il `MainPage` deriva dalla classe `ContentPage`, ma si noti il `partial` definizione di classe. Ne consegue che deve essere un'altra definizione di classe parziale per `MainPage`, ma in cui è? E che `InitializeComponent` metodo? 

Quando Visual Studio compila il progetto, analizza il file XAML per generare un file di codice c#. Se si osserva il **XamlSamples\XamlSamples\obj\Debug** directory, è disponibile un file denominato **XamlSamples.MainPage.xaml.g.cs**. È l'acronimo "g" per generata. Questa è la definizione di classe parziale altri di `MainPage` che contiene la definizione del `InitializeComponent` chiamato dal metodo di `MainPage` costruttore. Questi due parziale `MainPage` le definizioni di classe possono essere compilate insieme. A seconda se il codice XAML viene compilato o No, il file XAML o un formato binario del file XAML è incorporato nel file eseguibile.

In fase di esecuzione di codice nelle chiamate progetto specifico della piattaforma una `LoadApplication` metodo, passare una nuova istanza della `App` classe nella libreria .NET Standard. Il `App` crea un'istanza di costruttore di classe `MainPage`. Chiama il costruttore della classe `InitializeComponent`, che a sua volta chiama il `LoadFromXaml` metodo che consente di estrarre il file XAML (o il file binario compilato) dalla libreria .NET Standard. `LoadFromXaml` Inizializza tutti gli oggetti definiti nel file XAML, li connette tutti insieme in relazioni padre-figlio, gestori di eventi definito nel codice per eventi impostato nel file XAML e imposta la struttura degli oggetti risultante come il contenuto della pagina.

Sebbene in genere non occorre dedicare molto tempo con file di codice generati, talvolta runtime vengono generate eccezioni nel codice nel file generati, è necessario acquisire familiarità con esse.

Quando compili ed Esegui questo programma, il `Label` elemento viene visualizzato al centro della pagina, come suggerisce il codice XAML. Le tre piattaforme da sinistra a destra sono iOS, Android e UWP:

[![](get-started-with-xaml-images/xamlsamples.png "Predefinito visualizzato xamarin. Forms")](get-started-with-xaml-images/xamlsamples-large.png#lightbox "visualizzazione predefinito xamarin. Forms")

Per gli oggetti visivi più interessanti, è più interessante XAML.

## <a name="adding-new-xaml-pages"></a>Aggiunta di nuove pagine XAML

# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

Per aggiungere altri basate su XAML `ContentPage` classi al progetto, selezionare il **XamlSamples** libreria .NET Standard del progetto e richiamare il **progetto > Aggiungi nuovo elemento** voce di menu. A sinistra del **Aggiungi nuovo elemento** finestra di dialogo Seleziona **Visual c#** e **xamarin. Forms**. Nell'elenco selezionare **pagina contenuto** (non **pagina contenuto (c#)**, che consente di creare una pagina solo codice, o **visualizzazione contenuto**, che non è una pagina). Assegnare, ad esempio, un nome, la pagina **HelloXamlPage.xaml**:

![](get-started-with-xaml-images/win/addnewitemdialog.w157.png "Aggiungere una finestra di dialogo Nuovo elemento")

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio per Mac](#tab/vsmac)

Per aggiungere altri basate su XAML `ContentPage` classi al progetto, selezionare il **XamlSamples** libreria .NET Standard del progetto e richiamare il **File > Nuovo File** voce di menu. A sinistra del **nuovo File** finestra di dialogo Seleziona **form** a sinistra, e **form ContentPage Xaml** (non **form ContentPage**, che Crea una pagina solo codice, o **visualizzazione contenuto**, che non è una pagina). Assegnare, ad esempio, un nome, la pagina **HelloXamlPage**:

![](get-started-with-xaml-images/mac/newfiledialog.png "Nuova finestra di dialogo File")

-----

Due file vengono aggiunti al progetto, **HelloXamlPage.xaml** e il file code-behind **HelloXamlPage.xaml.cs**. 

## <a name="setting-page-content"></a>Contenuto della pagina impostazione

Modificare il **HelloXamlPage.xaml** file in modo che i tag soli sono quelli per `ContentPage` e `ContentPage.Content`:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.HelloXamlPage">
    <ContentPage.Content>
        
    </ContentPage.Content>
</ContentPage>
```

Il `ContentPage.Content` tag fanno parte della sintassi di XAML univoca. Inizialmente, appaiono come XML non valido, ma lo sono. Il periodo non è un carattere speciale nel codice XML.

Il `ContentPage.Content` tag vengono chiamati *elemento proprietà* tag. `Content` è una proprietà di `ContentPage`e in genere è impostata su una singola visualizzazione o un layout con visualizzazioni figlio. In genere le proprietà più attributi in XAML, ma sarebbe difficile da un `Content` dell'attributo a un oggetto complesso. Per questo motivo, la proprietà viene espressa come un elemento XML costituito il nome della classe e il nome di proprietà separati da un punto. A questo punto il `Content` proprietà può essere compreso tra il `ContentPage.Content` tag, simile al seguente:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.HelloXamlPage"
             Title="Hello XAML Page">
    <ContentPage.Content>

        <Label Text="Hello, XAML!"
               VerticalOptions="Center"
               HorizontalTextAlignment="Center"
               Rotation="-15"
               IsVisible="true"
               FontSize="Large"
               FontAttributes="Bold"
               TextColor="Blue" />

    </ContentPage.Content>
</ContentPage>
```

Si noti inoltre che un `Title` è stato impostato l'attributo nel tag radice.

In questo momento, la relazione tra classi e proprietà XML deve essere evidente: xamarin. Forms A classe (ad esempio `ContentPage` o `Label`) presente nel file XAML come elemento XML. Proprietà di tale classe, inclusi `Title` su `ContentPage` e sette proprietà di `Label`, in genere visualizzati come attributi XML.

Molti tasti di scelta rapida disponibili per impostare i valori di queste proprietà. Alcune proprietà sono tipi di dati di base: ad esempio, il `Title` e `Text` proprietà sono di tipo `String`, `Rotation` è di tipo `Double`, e `IsVisible` (ovvero `true` per impostazione predefinita e viene impostato solo per illustrazione) è di tipo `Boolean`.

Il `HorizontalTextAlignment` proprietà è di tipo `TextAlignment`, che è un'enumerazione. Per una proprietà di qualsiasi tipo di enumerazione, è sufficiente specificare un nome di membro.

Per le proprietà dei tipi più complessi, tuttavia, i convertitori di tipi vengono utilizzati per l'analisi XAML. Si tratta di classi in xamarin. Forms che derivano da `TypeConverter`. Molti sono le classi pubbliche, ma alcune non lo sono. Per questo particolare file XAML, alcune di queste classi svolgono un ruolo in background:

-  `LayoutOptionsConverter` per il `VerticalOptions` proprietà
-  `FontSizeConverter` per il `FontSize` proprietà
-  `ColorTypeConverter` per il `TextColor` proprietà

I convertitori di tipi che disciplinano la sintassi consentita delle impostazioni delle proprietà.

Il `ThicknessTypeConverter` in grado di gestire uno, due o quattro numeri separati da virgole. Se viene fornito un numero, si applica a tutti e quattro i lati. Con due numeri interi, il primo è left e right spaziatura interna e il secondo consiste nella parte superiore e inferiore. Quattro numeri sono espressi in ordine sinistro, superiore, destro e inferiore.

Il `LayoutOptionsConverter` possibile convertire i nomi dei campi statici pubblici del `LayoutOptions` struttura ai valori di tipo `LayoutOptions`.

Il `FontSizeConverter` in grado di gestire un `NamedSize` membro o una dimensione del carattere numerico.

Il `ColorTypeConverter` accetta i nomi dei campi statici pubblici del `Color` struttura o i valori RGB esadecimali, con o senza un canale alfa, preceduto da un simbolo di cancelletto (#). Di seguito è riportata la sintassi senza un canale alfa:

 `TextColor="#rrggbb"`

Ciascuna delle lettere minimo è una cifra esadecimale. Ecco come un canale alfa viene incluso:

 `TextColor="#aarrggbb">`

Per il canale alfa, tenere presente che è completamente opaco FF e 00 è completamente trasparente.

Due altri formati consentono di specificare una sola cifra esadecimale per ogni canale:

 `TextColor="#rgb"` `TextColor="#argb"`

In questi casi, la cifra viene ripetuta per formare il valore. Ad esempio, #CF3 è il colore RGB CC-FF-33.

## <a name="page-navigation"></a>Navigazione a pagina

Quando si esegue il **XamlSamples** programma, il `MainPage` viene visualizzato. Per visualizzare il nuovo `HelloXamlPage` è possibile impostare che come l'avvio di nuovo nella pagina di **App.xaml.cs** file o passare alla nuova pagina da `MainPage`.

Per implementare la navigazione, modificare innanzitutto codice il **App.xaml.cs** costruttore in modo che un `NavigationPage` viene creato l'oggetto:

```csharp
public App()
{
    InitializeComponent();
    MainPage = new NavigationPage(new MainPage());
}
```

Nel **MainPage.xaml.cs** costruttore, è possibile creare una semplice `Button` e utilizzare il gestore eventi per passare a `HelloXamlPage`:

```csharp
public MainPage()
{
    InitializeComponent();

    Button button = new Button
    {
        Text = "Navigate!",
        HorizontalOptions = LayoutOptions.Center,
        VerticalOptions = LayoutOptions.Center
    };

    button.Clicked += async (sender, args) =>
    {
        await Navigation.PushAsync(new HelloXamlPage());
    };

    Content = button;
}
```

L'impostazione di `Content` proprietà della pagina sostituisce l'impostazione del `Content` proprietà nel file XAML. Quando si compila e distribuisce la nuova versione di questo programma, un pulsante viene visualizzato sullo schermo. Ci si passa a `HelloXamlPage`. Di seguito è la pagina su iPhone, Android e UWP risultante:

[![](get-started-with-xaml-images/helloxaml1.png "Testo etichetta ruotato")](get-started-with-xaml-images/helloxaml1-large.png#lightbox "ruotare il testo etichetta")

È possibile tornare `MainPage` utilizzando il **< nuovamente** pulsante in iOS, utilizzando la freccia sinistra nella parte superiore della pagina o nella parte inferiore del telefono in Android o utilizzando la freccia sinistra nella parte superiore della pagina in Windows 10.

È possibile sperimentare il codice XAML per diversi modi eseguire il rendering di `Label`. Se è necessario incorporare il testo di tutti i caratteri Unicode, è possibile utilizzare la sintassi XML standard. Ad esempio, per inserire il messaggio introduttivo in inglesi, usare:

 `<Label Text="&#x201C;Hello, XAML!&#x201D;" … />`

Ecco l'aspetto seguente:

[![](get-started-with-xaml-images/helloxaml2.png "Etichetta di testo con caratteri Unicode ruotato")](get-started-with-xaml-images/helloxaml2-large.png#lightbox "ruotare il testo dell'etichetta con i caratteri Unicode")

## <a name="xaml-and-code-interactions"></a>XAML e le interazioni del codice

Il **HelloXamlPage** esempio contiene una sola `Label` nella pagina, ma ciò è insolito. La maggior parte delle `ContentPage` set derivati il `Content` ordinare un layout di alcune proprietà, ad esempio un `StackLayout`. Il `Children` proprietà del `StackLayout` è definito per essere di tipo `IList<View>` ma è effettivamente un oggetto di tipo `ElementCollection<View>`, e che può essere popolati insieme con più viste o altri layout. In XAML, vengono stabilite le relazioni padre-figlio con normale gerarchia XML. Ecco un file XAML per una nuova pagina denominata **XamlPlusCodePage**:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.XamlPlusCodePage"
             Title="XAML + Code Page">
    <StackLayout>
        <Slider VerticalOptions="CenterAndExpand" />

        <Label Text="A simple Label"
               Font="Large"
               HorizontalOptions="Center"
               VerticalOptions="CenterAndExpand" />

        <Button Text="Click Me!"
                HorizontalOptions="Center"
                VerticalOptions="CenterAndExpand" />
    </StackLayout>
</ContentPage>
```

Questo file XAML è la sintassi completato ed ecco l'aspetto seguente:

[![](get-started-with-xaml-images/xamlpluscode1.png "Più controlli in una pagina")](get-started-with-xaml-images/xamlpluscode1-large.png#lightbox "più controlli in una pagina")

Tuttavia, probabile che vengano considerare questo programma per essere funzionalmente mancanti. Ad esempio il `Slider` dovrebbe per causare il `Label` per visualizzare il valore corrente e `Button` probabilmente deve eseguire un'operazione all'interno del programma.

Come si vedrà [parte 4. Nozioni fondamentali sull'associazione dati](~/xamarin-forms/xaml/xaml-basics/data-binding-basics.md), il processo di visualizzazione di un `Slider` valore utilizzando un `Label` possono essere gestite interamente in XAML con un'associazione dati. Ma è utile visualizzare innanzitutto la soluzione di codice. Anche in questo caso, la gestione di `Button` richiede codice fare clic su. Ciò significa che il file code-behind per `XamlPlusCodePage` deve contenere i gestori per il `ValueChanged` evento del `Slider` e `Clicked` evento del `Button`. Verrà quindi aggiunto:

```csharp
namespace XamlSamples
{
    public partial class XamlPlusCodePage
    {
        public XamlPlusCodePage()
        {
            InitializeComponent();
        }

        void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
        {

        }

        void OnButtonClicked(object sender, EventArgs args)
        {

        }
    }
}
```

Questi gestori eventi non è necessario essere pubblici.

Nel file XAML, il `Slider` e `Button` è necessario includere gli attributi per i tag di `ValueChanged` e `Clicked` gli eventi che fanno riferimento a questi gestori:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.XamlPlusCodePage"
             Title="XAML + Code Page">
    <StackLayout>
        <Slider VerticalOptions="CenterAndExpand"
                ValueChanged="OnSliderValueChanged" />

        <Label Text="A simple Label"
               Font="Large"
               HorizontalOptions="Center"
               VerticalOptions="CenterAndExpand" />

        <Button Text="Click Me!"
                HorizontalOptions="Center"
                VerticalOptions="CenterAndExpand"
                Clicked="OnButtonClicked" />
    </StackLayout>
</ContentPage>
```

Si noti che l'assegnazione di un gestore a un evento ha la stessa sintassi di assegnazione di un valore a una proprietà.

Se il gestore per il `ValueChanged` evento del `Slider` verrà utilizzato il `Label` per visualizzare il valore corrente, il gestore deve fare riferimento a tale oggetto dal codice. Il `Label` è necessario un nome, che viene specificato con il `x:Name` attributo.

```xaml
<Label x:Name="valueLabel"
       Text="A simple Label"
       Font="Large"
       HorizontalOptions="Center"
       VerticalOptions="CenterAndExpand" />
```

Il `x` prefisso di `x:Name` attributo indica che questo attributo è intrinseco in XAML.

Il nome assegnato per il `x:Name` presenta le stesse regole come nomi di variabili c#. Ad esempio, deve iniziare con una lettera o un carattere di sottolineatura e non contenere spazi.

A questo punto il `ValueChanged` gestore eventi può impostare il `Label` per visualizzare il nuovo `Slider` valore. Il nuovo valore è disponibile dagli argomenti dell'evento:

```csharp
void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
{
    valueLabel.Text = args.NewValue.ToString("F3");
}
```

O, il gestore è stato possibile ottenere il `Slider` oggetto che genera l'evento dal `sender` argomento e ottenere il `Value` che proprietà:

```csharp
void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
{
    valueLabel.Text = ((Slider)sender).Value.ToString("F3");
}
```

Quando si esegue prima il programma, il `Label` non viene visualizzato il `Slider` valore perché il `ValueChanged` ancora non è stato generato l'evento. Ma qualsiasi manipolazione del `Slider` fa sì che il valore da visualizzare:

[![](get-started-with-xaml-images/xamlpluscode2.png "Dispositivo di scorrimento valore visualizzato")](get-started-with-xaml-images/xamlpluscode2-large.png#lightbox "dispositivo di scorrimento valore visualizzato")

Ora per il `Button`. Consente di simulare una risposta a un `Clicked` evento visualizzando un avviso con il `Text` del pulsante. Il gestore dell'evento può eseguire il cast sicuro di `sender` argomento a un `Button` e quindi accedere alle relative proprietà:

```csharp
async void OnButtonClicked(object sender, EventArgs args)
{
    Button button = (Button)sender;
    await DisplayAlert("Clicked!",
        "The button labeled '" + button.Text + "' has been clicked",
        "OK");
}
```

Il metodo è definito come `async` perché il `DisplayAlert` metodo è asincrono e devono essere preceduto dal `await` operatore, che restituisce al completamento del metodo. Poiché questo metodo ottiene il `Button` che genera l'evento dal `sender` argomento, lo stesso gestore può essere usato per più pulsanti.

Si è visto che un oggetto definito in XAML può generare un evento che viene gestito nel file code-behind e che il file code-behind può accedere a un oggetto definito in XAML tramite il nome assegnato a esso con il `x:Name` attributo. Si tratta di due metodi fondamentali che interagiscono codice e XAML.

Alcune informazioni aggiuntive in modo possibile potranno works XAML esaminando appena generato **XamlPlusCode.xaml.g.cs file**, che ora include qualsiasi nome assegnato a qualsiasi `x:Name` attributo come un campo privato. Di seguito è riportata una versione semplificata del file:

```csharp
public partial class XamlPlusCodePage : ContentPage {

    private Label valueLabel;

    private void InitializeComponent() {
        this.LoadFromXaml(typeof(XamlPlusCodePage));
        valueLabel = this.FindByName<Label>("valueLabel");
    }
}
```

La dichiarazione di questo campo consente la variabile liberamente utilizzabile in un punto qualsiasi all'interno di `XamlPlusCodePage` file di classe parziale sotto la giurisdizione. In fase di esecuzione, il campo è assegnato dopo il codice XAML è stato analizzato. Ciò significa che il `valueLabel` campo `null` quando il `XamlPlusCodePage` costruttore inizia ma validi dopo `InitializeComponent` viene chiamato.

Dopo aver `InitializeComponent` restituisce il controllo torna al costruttore, gli oggetti visivi della pagina costruiti come se fosse stata creata un'istanza e inizializzati nel codice. Il file XAML non è più svolge alcun ruolo nella classe. È possibile modificare questi oggetti nella pagina in modo che si desidera, ad esempio, tramite l'aggiunta di visualizzazioni per il `StackLayout`, o impostazione di `Content` proprietà della pagina da un altro elemento completamente. È possibile "esaminare l'albero" esaminando il `Content` proprietà della pagina e gli elementi di `Children` raccolte di layout. È possibile impostare le proprietà accessibile in questo modo le viste o assegnarvi gestori eventi in modo dinamico.

È possibile. È la pagina e XAML è solo uno strumento per creare il relativo contenuto.

## <a name="summary"></a>Riepilogo

Con questa introduzione, si è visto come un file XAML e un file di codice contribuiscono a una definizione di classe e come interagiscono i file XAML e codice. Ma XAML ha anche i proprio sintattici caratteristiche che consentono di utilizzare in modo estremamente flessibile. È possibile iniziare a esplorare queste [parte 2. Sintassi XAML essenziali](~/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax.md).



## <a name="related-links"></a>Collegamenti correlati

- [XamlSamples](https://developer.xamarin.com/samples/xamarin-forms/XamlSamples/)
- [Parte 2. Sintassi XAML essenziale](~/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax.md)
- [Parte 3. Estensioni di markup XAML](~/xamarin-forms/xaml/xaml-basics/xaml-markup-extensions.md)
- [Parte 4. Nozioni di base sul data binding](~/xamarin-forms/xaml/xaml-basics/data-binding-basics.md)
- [Parte 5. Da un'associazione dati a MVVM](~/xamarin-forms/xaml/xaml-basics/data-bindings-to-mvvm.md)
