---
title: mtouch
ms.topic: article
ms.prod: xamarin
ms.assetid: BCA491DA-E4C1-8689-3EC9-E4C72495A798
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.openlocfilehash: b1b61e7ce1bae413f132cfe1e6c051a53b786f98
ms.sourcegitcommit: 6cd40d190abe38edd50fc74331be15324a845a28
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2018
---
# <a name="mtouch"></a>mtouch


Le applicazioni per iPhone vengono fornite come bundle dell'applicazione. Si tratta di directory con estensione `.app` che contengono il codice, i dati, i file di configurazione e un manifesto, che l'iPhone usa per acquisire informazioni sull'applicazione.

Il processo di conversione di un eseguibile .NET in applicazione viene per lo più eseguito dal comando `mtouch`, uno strumento che integra molti dei passaggi necessari per convertire l'applicazione in bundle. Questo strumento viene usato anche per avviare l'applicazione nel simulatore e per distribuire il software in un dispositivo touch iPhone o iPod reale.


## <a name="detailed-instructions"></a>Istruzioni dettagliate

Consultare la pagina del manuale di [mtouch(1)](http://docs.go-mono.com/?link=man%3amtouch(1)), che contiene informazioni su tutti i possibili usi dello strumento mtouch.


## <a name="building"></a>Compilazione

Il comando `mtouch` può compilare il codice in tre modi diversi:

-  Compilare il codice per i test del simulatore.
-  Compilare il codice per la distribuzione del dispositivo.
-  Distribuire l'eseguibile nel dispositivo.


### <a name="building-for-the-simulator"></a>Compilazione per il simulatore

Quando si inizia, lo scenario usato più spesso consiste nel provare l'applicazione nel simulatore, quindi nell'usare `mtouch -sim` per compilare il codice in un pacchetto del simulatore. Ecco come:

```bash
$ mtouch -sim Hello.app hello.exe
```

### <a name="building-for-the-device"></a>Compilazione per il dispositivo

Per compilare il software per il dispositivo, è necessario compilare l'applicazione usando l'opzione `mtouch -dev` e specificare inoltre il nome del certificato usato per firmare l'applicazione. Il codice seguente mostra in che modo viene compilata l'applicazione per il dispositivo:

```bash
$ mtouch -dev -c "iPhone Developer: Miguel de Icaza" foo.exe
```

In questo caso specifico, viene usato il certificato "iPhone Developer: Miguel de Icaza" per firmare l'applicazione. Questo passaggio è molto importante o il dispositivo fisico rifiuterà di caricare l'applicazione.

 <a name="Running_your_Application" />


## <a name="running-your-application"></a>Esecuzione dell'applicazione


### <a name="launching-on-the-simulator"></a>Avvio nel simulatore

L'avvio nel simulatore è molto semplice quando è disponibile un bundle dell'applicazione:

```bash
$ mtouch --sdkroot /Applications/Xcode.app -launchsim Hello.app 
```

Se il flag `--sdkroot` non è impostato, per impostazione predefinita viene usato il percorso xcode-select e viene restituito l'avviso seguente:

> eg: warning MT0061: No Xcode.app specified (using --sdkroot), using the system Xcode as reported by 'xcode-select --print-path': /Applications/Xcode.app/Contents/Developer 

La riga di comando precedente produce un output simile al seguente:

```bash
Launching application
Application launched
PID: 98460
Press enter to terminate the application
```



È consigliabile mantenere un log dei file di output standard e dei file di errore standard per semplificare il debug. L'output di `Console.WriteLine` passa a `stdout`, mentre l'output di `Console.Error.WriteLine` e qualsiasi messaggio di errore di runtime passano a `stderr`.

A questo scopo, usare i flag `--stdout` e `--stderr`:

```bash
../../tools/mtouch/mtouch --launchsim=Hello.app --stdout=output --stderr=error
```

Se l'applicazione non riesce, è possibile visualizzare l'output e l'errore per diagnosticare il problema.


### <a name="deploying-to-a-device"></a>Distribuzione a un dispositivo

Per distribuire l'applicazione nel dispositivo, è necessario effettuare il provisioning del dispositivo in base a quanto descritto nel documento sulla [gestione dei dispositivi](http://developer.apple.com/library/ios/#documentation/Xcode/Conceptual/ios_development_workflow/00-About_the_iOS_Application_Development_Workflow/introduction.html) di Apple. Dopo aver completato correttamente il provisioning del dispositivo, è possibile usare il comando mtouch per distribuire un bundle ".app" compilato nel dispositivo. A questo scopo, usare questo comando:

```bash
$ mtouch —sdkroot /Applications/Xcode.app -installdev=MyApp.app
```

Se il flag `--sdkroot` non è impostato, per impostazione predefinita viene usato il percorso xcode-select e viene restituito l'avviso seguente:

> eg: warning MT0061: No Xcode.app specified (using --sdkroot), using the system Xcode as reported by 'xcode-select --print-path': /Applications/Xcode.app/Contents/Developer 

Questi passaggi vengono in genere eseguiti da Visual Studio per Mac.

## <a name="reference"></a>Riferimenti

Per informazioni dettagliate su altre opzioni della riga di comando, vedere la pagina del manuale di [mtouch(1)](http://docs.go-mono.com/?link=man%3amtouch(1)).



## <a name="related-links"></a>Collegamenti correlati

- [mtouch(1)](http://iosapi.xamarin.com/?link=man%3amtouch(1))