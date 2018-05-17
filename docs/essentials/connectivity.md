---
title: Connettività Xamarin.Essentials
description: La classe connettività consente di monitorare le modifiche nelle condizioni di rete del dispositivo, verificare l'accesso alla rete corrente e modo in cui è attualmente connesso.
ms.assetid: E1B1F152-B1D5-4227-965E-C0AEBF528F49
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: d2184f1e9817b473eac1d0b69a7637bc862de4cf
ms.sourcegitcommit: 3e05b135b6ff0d607bc2378c1b6e66d2eebbcc3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2018
---
# <a name="xamarinessentials-connectivity"></a>Connettività Xamarin.Essentials

![Versione non definitiva NuGet](~/media/shared/pre-release.png)

Il **connettività** consente di classe monitorare per le modifiche nelle condizioni di rete del dispositivo, controllare l'accesso alla rete corrente e modo in cui è attualmente connesso.

## <a name="getting-started"></a>Introduzione

Per l'accesso di **connettività** è necessaria la funzionalità le seguenti impostazioni specifiche della piattaforma.

# <a name="androidtabandroid"></a>[Android](#tab/android)

Il `AccessNetworkState` l'autorizzazione è obbligatorio e deve essere configurata nel progetto Android. Questo può essere aggiunto nei modi seguenti:

Aprire la **AssemblyInfo.cs** file sotto il **proprietà** cartella e aggiungere:

```csharp
[assembly: UsesPermission(Android.Manifest.Permission.AccessNetworkState)]
```

O aggiornare il manifesto Android:

Aprire la **androidmanifest. XML** file sotto il **proprietà** cartella e aggiungere il codice seguente all'interno del **manifesto** nodo.

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Oppure fare clic con il pulsante destro sul progetto di piattaforma Android e aprire le proprietà del progetto. Sotto **manifesto Android** trovare il **delle autorizzazioni necessarie:** area e verificare il **stato di accesso rete** l'autorizzazione. Verrà automaticamente aggiornato il **Androidmanifest** file.

# <a name="iostabios"></a>[iOS](#tab/ios)

Non è necessaria alcuna configurazione aggiuntiva.

# <a name="uwptabuwp"></a>[PIATTAFORMA UWP](#tab/uwp)

Non è necessaria alcuna configurazione aggiuntiva.

-----

## <a name="using-connectivity"></a>Utilizzo di connettività

Aggiungere un riferimento a Xamarin.Essentials nella classe:

```csharp
using Xamarin.Essentials;
```

Controllare l'accesso alla rete corrente:

```csharp
var current = Connectivity.NetworkAccess;

if (current == NetworkAccess.Internet)
{
    // Connection to internet is available
}
```

[L'accesso alla rete](xref:Xamarin.Essentials.NetworkAccess) rientra nelle categorie seguenti:

* **Internet** : l'accesso locale e internet.
* **ConstrainedInternet** – limitato l'accesso a internet. Indica vincolato la connettività del portale, in cui viene fornito l'accesso locale a un portale web, ma l'accesso a Internet richiede che vengano fornite credenziali specifiche tramite un portale.
* **Locale** : locale solo l'accesso alla rete.
* **Nessuno** – nessuna connettività è disponibile.
* **Sconosciuto** : Impossibile determinare la connettività internet.

È possibile controllare il tipo di [profilo di connessione](xref:Xamarin.Essentials.ConnectionProfile) sta utilizzando attivamente il dispositivo:

```csharp
var profiles = Connectivity.Profiles;
if (profiles.Contains(ConnectionProfile.WiFi))
{
    // Active Wi-Fi connection.
}
```

Ogni volta che il profilo di connessione o rete accedere alle modifiche è possibile ricevere un evento all'attivazione:

```csharp
public class ConnectivityTest
{
    public ConnectivityTest()
    {
        // Register for connectivity changes, be sure to unsubscribe when finished
        Connectivity.ConnectivityChanged += Connectivity_ConnectivityChanged;
    }

    void Connectivity_ConnectivityChanged(ConnectivityChangedEventArgs  e)
    {
        var access = e.NetworkAccess;
        var profiles = e.Profiles;
    }
}
```

## <a name="limitations"></a>Limitazioni

È importante notare che è possibile che `Internet` viene segnalato da `NetworkAccess` ma l'accesso completo al web non è disponibile. A causa di funzionamento di connettività in ciascuna piattaforma solo possibile garantire che sia disponibile una connessione. Ad esempio il dispositivo può essere collegato a una rete Wi-Fi, ma il router è disconnesso da internet. In questa istanza possono essere riportati Internet, ma non è disponibile una connessione attiva.

## <a name="api"></a>API

* [Codice sorgente di connettività](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/Connectivity)
* [Documentazione API di connettività](xref:Xamarin.Essentials.Connectivity)