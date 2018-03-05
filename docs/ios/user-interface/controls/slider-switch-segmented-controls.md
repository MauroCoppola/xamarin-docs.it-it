---
title: Dispositivi di scorrimento, commutatori e controlli segmentati
ms.topic: article
ms.prod: xamarin
ms.assetid: 85BF0EC8-E581-49CD-B9E7-98BE4C5A0F6B
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/21/2017
ms.openlocfilehash: 1c24b1faf7b108466d6e93ffae8112d0dea6d844
ms.sourcegitcommit: 6cd40d190abe38edd50fc74331be15324a845a28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="sliders-switches-and-segmented-controls"></a>Dispositivi di scorrimento, commutatori e controlli segmentati

<a name="Sliders" />


## <a name="sliders"></a>Dispositivi di scorrimento

Il dispositivo di scorrimento consente di selezione semplice di un valore numerico in un intervallo. Il controllo predefinito per un valore compreso tra 0 e 1, ma questi limiti possono essere personalizzati.

 [ ![](slider-switch-segmented-controls-images/image25a.png "Slider")](slider-switch-segmented-controls-images/image25a.png)

Nella schermata seguente vengono illustrate le proprietà che possono essere modificate nella finestra di progettazione:

 [ ![](slider-switch-segmented-controls-images/image26a.png "Proprietà dispositivo di scorrimento")](slider-switch-segmented-controls-images/image25a.png)

È possibile impostare questi valori nel codice, come illustrato di seguito, inclusi il collegamento di un gestore per visualizzare il valore attualmente selezionato in un `UILabel` controllo:

```csharp
slider1.MinValue = -1;
slider1.MaxValue = 2;
slider1.Value = 0.5f; // the current value
slider1.ValueChanged += (sender,e) => label1.Text = ((UISlider)sender).Value.ToString ();
```

È anche possibile personalizzare l'aspetto visivo del dispositivo di scorrimento impostazione

```csharp
slider1.ThumbTintColor = UIColor.Blue;
slider1.MinimumTrackTintColor = UIColor.Gray;
slider1.MaximumTrackTintColor = UIColor.Green;
```

Il dispositivo di scorrimento personalizzato è simile al seguente:

 [ ![](slider-switch-segmented-controls-images/image27a.png "Dispositivo di scorrimento personalizzato")](slider-switch-segmented-controls-images/image28a.png)

> [!IMPORTANT]
> Al momento è presente un [bug](http://stackoverflow.com/a/19496179) causando il `ThumbTint` per non eseguire il rendering in fase di esecuzione come previsto. È possibile aggiungere la seguente riga di codice **prima** al codice precedente come soluzione alternativa. [[Origine](http://stackoverflow.com/a/21396794)]:
>
> `slider1.SetThumbImage(UIImage.FromBundle("thumb.png"),UIControlState.Normal);`
> 
> È possibile utilizzare qualsiasi immagine, come verrà sottoposto a override, ma assicurarsi che quest'ultima sia _in_ directory delle risorse e viene chiamato nel codice.

<a name="Switch" />

## <a name="switch"></a>Opzione

iOS utilizza il `UISwitch` come input di un valore booleano che può essere rappresentato da un pulsante di opzione in altre piattaforme. L'utente può modificare il controllo spostando il *thumb* tra il **On/Off** posizioni.

 [ ![](slider-switch-segmented-controls-images/image28a.png "commutatore")](slider-switch-segmented-controls-images/image28a.png)

L'aspetto del commutatore può essere personalizzato nel **proprietà riempimento** della finestra di progettazione, che consentirà di controllare lo stato predefinito, **On/Off tint** colori e un **on/off immagine**. Come illustrato nell'immagine riportata di seguito:

 [ ![](slider-switch-segmented-controls-images/image29a.png "Proprietà del commutatore")](slider-switch-segmented-controls-images/image29a.png)

Le proprietà del commutatore possono essere impostate anche nel codice, ad esempio il codice riportato di seguito verrà mostrato un interruttore con il valore predefinito di `On`:

```csharp
switch1.On = true;
```

 <a name="Segmented_Controls" />


## <a name="segmented-controls"></a>Controlli segmentati

Un controllo segmentata è un modo organizzato per consentire agli utenti di interagire con un numero ridotto di opzioni. È disposto orizzontalmente e ogni segmento funziona come un pulsante separato. Quando si utilizza la finestra di progettazione, il controllo segmentata è reperibile nella **della casella degli strumenti > controlli**e dovrebbe essere come nell'immagine seguente:

 [ ![](slider-switch-segmented-controls-images/segmentedcontrol.png "Controllo segmentato")](slider-switch-segmented-controls-images/segmentedcontrol.png)

Consente di una caratteristica unica della finestra di progettazione per ogni segmento di essere selezionate singolarmente nella finestra di progettazione, come illustrato di seguito:

 [ ![](slider-switch-segmented-controls-images/segmentedcontrolselection.png "Controllo segmentato")](slider-switch-segmented-controls-images/segmentedcontrolselection.png)

In questo modo il riquadro proprietà da utilizzare per controllare in modo più preciso le proprietà di ogni segmento. È possibile visualizzare le proprietà modificabili nella schermata seguente:

 [ ![](slider-switch-segmented-controls-images/segmentedcontrolproperties.png "Controllo segmentato")](slider-switch-segmented-controls-images/segmentedcontrolproperties.png)

Si noti che lo stile del controllo segmentata sono deprecato in iOS7, e quindi modificare le opzioni per l'oggetto in un'applicazione IOS 7 non avranno effetto.

## <a name="related-links"></a>Collegamenti correlati

- [Controlli (esempio)](https://developer.xamarin.com/samples/Controls/)
- [Avvisi Controller](https://developer.xamarin.com/recipes/ios/standard_controls/alertcontroller/)