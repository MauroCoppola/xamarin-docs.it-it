---
title: Compilazione XAML in xamarin. Forms
description: Questo articolo illustra come XAML può essere compilato direttamente in linguaggio intermedio (IL) con il compilatore di xamarin. Forms XAML (XAMLC).
ms.prod: xamarin
ms.assetid: 9A2D10A6-5DFC-485F-A75A-2F7B98314025
ms.technology: xamarin-forms
author: charlespetzold
ms.author: chape
ms.date: 07/02/2018
ms.openlocfilehash: b828e62ef1037bf47a2ae5fb303fbf8fcace6549
ms.sourcegitcommit: 6e955f6851794d58334d41f7a550d93a47e834d2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38997133"
---
# <a name="xaml-compilation-in-xamarinforms"></a>Compilazione XAML in xamarin. Forms

_XAML può essere compilato direttamente in linguaggio intermedio (IL) con il compilatore XAML (XAMLC)._

XAMLC offre alcuni vantaggi:

- Esegue il controllo del codice XAML in fase di compilazione, notificando all'utente eventuali errori.
- Rimuove parte del tempo di carico e di creazione dell'istanza per gli elementi XAML.
- Consente di ridurre le dimensioni del file dell'assembly finale non includendo più i file XAML.

XAMLC è disabilitato per impostazione predefinita per garantire la compatibilità con le versioni precedenti. Può essere abilitata a livello di assembly e di classe aggiungendo il `XamlCompilation` attributo.

Esempio di codice seguente viene illustrato come consentire XAMLC a livello di assembly:

```csharp
using Xamarin.Forms.Xaml;
...
[assembly: XamlCompilation (XamlCompilationOptions.Compile)]
namespace PhotoApp
{
  ...
}
```

In questo esempio, controllo di tutto il XAML contenute all'interno dell'assembly in fase di compilazione verrà eseguita con errori XAML da segnalare in fase di compilazione anziché in fase di esecuzione. Pertanto, il `assembly` come prefisso il `XamlCompilation` attributo specifica che l'attributo viene applicato all'intero assembly.

Esempio di codice seguente viene illustrato come consentire XAMLC a livello di classe:

```csharp
using Xamarin.Forms.Xaml;
...
[XamlCompilation (XamlCompilationOptions.Compile)]
public class HomePage : ContentPage
{
  ...
}
```

In questo esempio, il controllo del XAML per la fase di compilazione il `HomePage` classe verrà eseguita e gli errori segnalati come parte del processo di compilazione.

> [!NOTE]
> Il `XamlCompilation` attributo e il `XamlCompilationOptions` enumerazione si trovano nel `Xamarin.Forms.Xaml` dello spazio dei nomi, che deve essere importato per usarli.


## <a name="related-links"></a>Collegamenti correlati

- [XamlCompilation](xref:Xamarin.Forms.Xaml.XamlCompilationAttribute)
- [XamlCompilationOptions](xref:Xamarin.Forms.Xaml.XamlCompilationOptions)
