---
title: I tipi di riempimento del percorso
description: Questo articolo esamina i diversi effetti possibili con i tipi di riempimento di SkiaSharp percorso e questo concetto è illustrato con esempio di codice.
ms.prod: xamarin
ms.assetid: 57103A7A-49A2-46AE-894C-7C2664682644
ms.technology: xamarin-skiasharp
author: charlespetzold
ms.author: chape
ms.date: 03/10/2017
ms.openlocfilehash: 17043054c920a69570f38b227d05980494e29139
ms.sourcegitcommit: 12d48cdf99f0d916536d562e137d0e840d818fa1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39615470"
---
# <a name="the-path-fill-types"></a>I tipi di riempimento del percorso

_Individua i diversi effetti possibili con i tipi di riempimento percorso SkiaSharp_

Può essere sovrapposto due distribuzioni in un percorso e le righe che compongono una distribuzione del singolo possono sovrapporsi. Può quindi essere riempito potenzialmente qualsiasi area inclusa, ma è possibile evitare di riempire tutte le aree racchiusi. Di seguito è riportato un esempio:

![](fill-types-images/filltypeexample.png "Cinque punte filles parzialmente a stelle")

È necessario un po' controllare. L'algoritmo di riempimento è disciplinato dalle [ `SKFillType` ](https://developer.xamarin.com/api/property/SkiaSharp.SKPath.FillType/) proprietà della `SKPath`, che è impostata su un membro del [ `SKPathFillType` ](https://developer.xamarin.com/api/type/SkiaSharp.SKPathFillType/) enumerazione:

- [`Winding`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathFillType.Winding/), il valore predefinito
- [`EvenOdd`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathFillType.EvenOdd/)
- [`InverseWinding`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathFillType.InverseWinding/)
- [`InverseEvenOdd`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathFillType.InverseEvenOdd/)

Entrambi gli algoritmi dei vertici e coppie determinano se qualsiasi area racchiusa viene compilata o non compilato in base a un'ipotetica linea tracciata da quell'area verso l'infinito. Tale riga attraversa uno o più righe di limiti che costituiscono il percorso. Con la modalità dei vertici, se non è il numero di linee dei bordi disegnata in equilibrio di una sola direzione il numero delle linee disegnate in altra direzione, l'area riempita. In caso contrario, l'area viene riempita. L'algoritmo coppie riempie un'area, se il numero di righe di limiti è dispari.

Con tutti i percorsi di routine, l'algoritmo dei vertici riempie spesso tutte le aree racchiusa di un percorso. L'algoritmo coppie produce in genere risultati più interessanti.

L'esempio classico è una stella a 5 punte, come illustrato nel **Five-Pointed Star** pagina. Il [FivePointedStarPage.xaml](https://github.com/xamarin/xamarin-forms-samples/blob/master/SkiaSharpForms/Demos/Demos/SkiaSharpFormsDemos/LinesAndPaths/FivePointedStarPage.xaml) un'istanza di file due `Picker` viste per selezionare il percorso è riempire tipo e se il percorso viene tracciato o compilato o entrambi e in quale ordine:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:skia="clr-namespace:SkiaSharp.Views.Forms;assembly=SkiaSharp.Views.Forms"
             x:Class="SkiaSharpFormsDemos.FivePointedStarPage"
             Title="Five-Pointed Star">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>

        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>

        <Picker x:Name="fillTypePicker"
                Title="Path Fill Type"
                Grid.Row="0"
                Grid.Column="0"
                Margin="10"
                SelectedIndexChanged="OnPickerSelectedIndexChanged">
            <Picker.Items>
                <x:String>Winding</x:String>
                <x:String>EvenOdd</x:String>
                <x:String>InverseWinding</x:String>
                <x:String>InverseEvenOdd</x:String>
            </Picker.Items>
            <Picker.SelectedIndex>
                0
            </Picker.SelectedIndex>
        </Picker>

        <Picker x:Name="drawingModePicker"
                Title="Drawing Mode"
                Grid.Row="0"
                Grid.Column="1"
                Margin="10"
                SelectedIndexChanged="OnPickerSelectedIndexChanged">
            <Picker.Items>
                <x:String>Fill only</x:String>
                <x:String>Stroke only</x:String>
                <x:String>Stroke then Fill</x:String>
                <x:String>Fill then Stroke</x:String>
            </Picker.Items>
            <Picker.SelectedIndex>
                0
            </Picker.SelectedIndex>
        </Picker>

        <skia:SKCanvasView x:Name="canvasView"
                           Grid.Row="1"
                           Grid.Column="0"
                           Grid.ColumnSpan="2"
                           PaintSurface="OnCanvasViewPaintSurface" />
    </Grid>
</ContentPage>
```

Il file code-behind Usa sia `Picker` valori a disegnare una stella a 5 punte:

```csharp
void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
{
    SKImageInfo info = args.Info;
    SKSurface surface = args.Surface;
    SKCanvas canvas = surface.Canvas;

    canvas.Clear();

    SKPoint center = new SKPoint(info.Width / 2, info.Height / 2);
    float radius = 0.45f * Math.Min(info.Width, info.Height);

    SKPath path = new SKPath
    {
        FillType = (SKPathFillType)Enum.Parse(typeof(SKPathFillType),
                        fillTypePicker.Items[fillTypePicker.SelectedIndex])
    };
    path.MoveTo(info.Width / 2, info.Height / 2 - radius);

    for (int i = 1; i < 5; i++)
    {
        // angle from vertical
        double angle = i * 4 * Math.PI / 5;
        path.LineTo(center + new SKPoint(radius * (float)Math.Sin(angle),
                                        -radius * (float)Math.Cos(angle)));
    }
    path.Close();

    SKPaint strokePaint = new SKPaint
    {
        Style = SKPaintStyle.Stroke,
        Color = SKColors.Red,
        StrokeWidth = 50,
        StrokeJoin = SKStrokeJoin.Round
    };

    SKPaint fillPaint = new SKPaint
    {
        Style = SKPaintStyle.Fill,
        Color = SKColors.Blue
    };

    switch (drawingModePicker.SelectedIndex)
    {
        case 0:
            canvas.DrawPath(path, fillPaint);
            break;

        case 1:
            canvas.DrawPath(path, strokePaint);
            break;

        case 2:
            canvas.DrawPath(path, strokePaint);
            canvas.DrawPath(path, fillPaint);
            break;

        case 3:
            canvas.DrawPath(path, fillPaint);
            canvas.DrawPath(path, strokePaint);
            break;
    }
}
```

In genere, il tipo di riempimento percorso dovrebbe influire sul solo riempimenti e non i tratti, ma i due `Inverse` influiscono sulla modalità sia riempimenti e tracce. Per i riempimenti, i due `Inverse` tipi riempire le aree oppositely in modo che l'area di fuori l'asterisco viene riempita. Per i tratti, i due `Inverse` tipi colore tutto ad eccezione del tratto. Utilizzo di questi tipi di riempimento inverso può produrre alcuni effetti dispari, come illustrato nella schermata di iOS:

[![](fill-types-images/fivepointedstar-small.png "Tripla screenshot della pagina di Star Five-Pointed")](fill-types-images/fivepointedstar-large.png#lightbox "tripla screenshot della pagina Five-Pointed Star")

Gli screenshot di Android e UWP vengono illustrati gli effetti dei vertici e coppie tipici, ma l'ordine del tratto e riempimento influisce anche sui risultati.

La direzione che vengono visualizzate linee dipende l'algoritmo dei vertici. In genere quando si crea un percorso, è possibile controllare tale direzione come specificato da righe sono rappresentate da un punto a altro. Tuttavia, il `SKPath` classe definisce inoltre metodi, ad esempio `AddRect` e `AddCircle` che disegnare i contorni interi. Per controllare come vengono disegnati questi oggetti, i metodi includono un parametro di tipo [ `SKPathDirection` ](https://developer.xamarin.com/api/type/SkiaSharp.SKPathDirection/), che contiene due membri:

- [`Clockwise`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathDirection.Clockwise/)
- [`CounterClockwise`](https://developer.xamarin.com/api/field/SkiaSharp.SKPathDirection.CounterClockwise/)

I metodi `SKPath` che includono un' `SKPathDirection` parametro assegnargli un valore predefinito di `Clockwise`.

Il **cerchi sovrapposti** pagina Crea un percorso con quattro cerchi sovrapposti con un tipo di riempimento coppie percorso:

```csharp
void OnCanvasViewPaintSurface(object sender, SKPaintSurfaceEventArgs args)
{
    SKImageInfo info = args.Info;
    SKSurface surface = args.Surface;
    SKCanvas canvas = surface.Canvas;

    canvas.Clear();

    SKPoint center = new SKPoint(info.Width / 2, info.Height / 2);
    float radius = Math.Min(info.Width, info.Height) / 4;

    SKPath path = new SKPath
    {
        FillType = SKPathFillType.EvenOdd
    };

    path.AddCircle(center.X - radius / 2, center.Y - radius / 2, radius);
    path.AddCircle(center.X - radius / 2, center.Y + radius / 2, radius);
    path.AddCircle(center.X + radius / 2, center.Y - radius / 2, radius);
    path.AddCircle(center.X + radius / 2, center.Y + radius / 2, radius);

    SKPaint paint = new SKPaint()
    {
        Style = SKPaintStyle.Fill,
        Color = SKColors.Cyan
    };

    canvas.DrawPath(path, paint);

    paint.Style = SKPaintStyle.Stroke;
    paint.StrokeWidth = 10;
    paint.Color = SKColors.Magenta;

    canvas.DrawPath(path, paint);
}
```

È un'immagine interessa creata con poche righe di codice:

[![](fill-types-images/overlappingcircles-small.png "Tripla screenshot della pagina di cerchi sovrapposti")](fill-types-images/overlappingcircles-large.png#lightbox "tripla screenshot della pagina di cerchi sovrapposti")


## <a name="related-links"></a>Collegamenti correlati

- [API di SkiaSharp](https://developer.xamarin.com/api/root/SkiaSharp/)
- [SkiaSharpFormsDemos (esempio)](https://developer.xamarin.com/samples/xamarin-forms/SkiaSharpForms/Demos/)
