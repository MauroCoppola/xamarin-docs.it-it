---
title: Debug di App xamarin. IOS con Xcode
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: 5FDDEDB3-AEB9-4D9C-9F7B-FEFAA9AF0031
ms.technology: xamarin-ios
author: migueldeicaza
ms.author: miguel
ms.date: 02/22/2018
ms.openlocfilehash: e0127d4b24236d350e5fa967110316544c320d0f
ms.sourcegitcommit: bf05041cc74fb05fd906746b8ca4d1403fc5cc7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2018
ms.locfileid: "39514708"
---
# <a name="debugging-xamarinios-apps-with-xcode"></a>Debug di App xamarin. IOS con Xcode

Potrebbero essere presenti scenari in cui si vuole usare Xcode per il debug di alcune parti dell'applicazione xamarin. IOS. Mentre non sarà in grado di eseguire il debug di codice .NET in esso, sarà comunque in grado di eseguire il debug di codice nativo e usare alcuni dei visualizzatori native in Xcode.

## <a name="walkthrough"></a>Procedura dettagliata

Se non è presente alcun supporto predefinito per il debug di Xcode in Visual Studio per Mac, è possibile utilizzare la procedura seguente per ottenere questo risultato:

1. Creare un'app per iOS Xcode con lo stesso ID bundle come quello nell'app Xamarin.
   
    - È possibile trovare l'identificatore del bundle del progetto xamarin. IOS, aprire il **Info. plist** file:

        ![Modifica file Info. plist](debugging-with-xcode-images/vsmac-infoplist.png "modifica Info.list")

    - In Xcode, impostare l'identificatore del bundle quando si crea il progetto oppure selezionando la destinazione del progetto:

        ![Impostare l'identificatore del Bundle in Xcode](debugging-with-xcode-images/xcode-bundle.png "impostando l'identificatore del Bundle in Xcode")

2. Modificare il progetto Xcode in attesa per il lancio invece di avviare automaticamente l'app:

    - Aprire il **Pannello di modifica dello schema** selezionando **prodotto > schema > Modifica combinazione** o utilizzando il **cmd⌘ + <** tasti di scelta rapida.

    - Selezionare il **eseguiti** lo schema e di destra del pannello è dovrebbe essere visualizzato **avviare** opzioni. Selezionare **attendere il file eseguibile da avviare** e fare clic su **Chiudi**.

        ![Attendere il file eseguibile da avviare](debugging-with-xcode-images/xcode-schemes.png "attendere eseguibile da avviare")

3. Eseguire il progetto Xcode.

    Questo verrà installato l'app Xcode fittizio nel dispositivo, ma non verrà avviate.

4. Eseguire l'app Xamarin.

    Xcode deve connettersi all'app Xamarin quando viene avviata.

### <a name="caveats"></a>Avvertenze

Potrebbe essere necessario apportare una piccola modifica all'app xamarin. IOS ogni volta che si avvia. In caso contrario, Visual Studio per Mac rileverà che l'app non deve necessariamente essere compilati *e* è già installato, e non sarà reinstallarlo tramite l'app fittizio di Xcode.

## <a name="alternative---using-lldb"></a>In alternativa - usando lldb

Se ha familiarità con **lldb** dalla riga di comando, è una soluzione più semplice.

Nella shell, digitare il comando seguente:

```bash
touch ~/.mtouch-launch-with-lldb
```

Si otterranno le istruzioni **Output applicazione** finestra sulle operazioni da eseguire, ma in pratica, quando si esegue l'applicazione, sarà possibile usare **lldb** dalla riga di comando per il debug dell'applicazione.
