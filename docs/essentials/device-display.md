---
title: 'Xamarin.Essentials: Informazioni di visualizzazione dispositivo'
description: Questo documento descrive la classe DeviceDisplay in Xamarin.Essentials, che fornisce metriche dello schermo del dispositivo in cui viene eseguita l'applicazione.
ms.assetid: 2821C908-C613-490D-8E8C-1BD3269FCEEA
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: cb42da4c8c2d0e381a5b00f7e60da6f427d19c66
ms.sourcegitcommit: 51c274f37369d8965b68ff587e1c2d9865f85da7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2018
ms.locfileid: "39353828"
---
# <a name="xamarinessentials-device-display-information"></a>Xamarin.Essentials: Informazioni di visualizzazione dispositivo

![Versione non definitiva NuGet](~/media/shared/pre-release.png)

Il **DeviceDisplay** classe fornisce informazioni sulle metriche di schermo del dispositivo cui è in esecuzione l'applicazione.

## <a name="using-devicedisplay"></a>Usando DeviceDisplay

Aggiungere un riferimento a Xamarin.Essentials nella classe:

```csharp
using Xamarin.Essentials;
```

## <a name="screen-metrics"></a>Metriche dello schermo

Oltre alle informazioni di base del dispositivo le **DeviceDisplay** classe contiene informazioni su schermo e l'orientamento del dispositivo.

```csharp
// Get Metrics
var metrics = DeviceDisplay.ScreenMetrics;

// Orientation (Landscape, Portrait, Square, Unknown)
var orientation = metrics.Orientation;

// Rotation (0, 90, 180, 270)
var rotation = metrics.Rotation;

// Width (in pixels)
var width = metrics.Width;

// Height (in pixels)
var height = metrics.Height;

// Screen density
var density = metrics.Density;
```

Il **DeviceDisplay** classe espone inoltre un evento che può essere sottoscritti che viene attivato ogni volta che una schermata di modifiche delle metriche:

```csharp
public class ScreenMetricsTest
{
    public ScreenMetricsTest()
    {
        // Subscribe to changes of screen metrics
        DeviceDisplay.ScreenMetricsChanged += OnScreenMetricsChanged;
    }

    void OnScreenMetricsChanged(ScreenMetricsChangedEventArgs  e)
    {
        // Process changes
        var metrics = e.Metrics;
    }
}
```

## <a name="api"></a>API

- [Codice sorgente DeviceDisplay](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/DeviceDisplay)
- [Documentazione dell'API DeviceDisplay](xref:Xamarin.Essentials.DeviceDisplay)
