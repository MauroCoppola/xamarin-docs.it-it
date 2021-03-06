---
title: Registrazione di un'impronta digitale
description: Come impostare backup di un blocco dello schermo e si registra un'impronta digitale in un emulatore o dispositivo Android.
ms.prod: xamarin
ms.assetid: 52092F63-00EE-4F8B-A49F-65C9CCBA7EF2
ms.technology: xamarin-android
author: mgmclemore
ms.author: mamcle
ms.date: 02/16/2018
ms.openlocfilehash: 4faee5decb102d17d9a270b96cef4a12fc9dbef4
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
ms.locfileid: "30762334"
---
# <a name="enrolling-a-fingerprint"></a>Registrazione di un'impronta digitale

## <a name="enrolling-a-fingerprint-overview"></a>Registrazione di una panoramica delle impronte digitali

È possibile solo per un'applicazione Android di usare l'autenticazione impronta digitale se il dispositivo è già stato configurato con l'autenticazione impronta digitale. Questa Guida verrà illustrato come registrare un'impronta digitale in un emulatore o dispositivo Android. Gli emulatori non dispone di hardware effettivo per eseguire un'analisi delle impronte digitali, ma è possibile simulare un'analisi delle impronte digitali con l'aiuto del Bridge Debug Android (descritte di seguito).  Questa Guida verrà illustrate le procedure abilitare il blocco dello schermo in un dispositivo Android e si registra un'impronta digitale per l'autenticazione.

## <a name="requirements"></a>Requisiti

Per registrare un'impronta digitale, è necessario disporre di un dispositivo Android o un emulatore in esecuzione il livello API 23 (Android 6.0).

L'utilizzo di Android Debug Bridge (ADB) richiede una certa familiarità con il prompt dei comandi e **adb** eseguibile deve essere il percorso del Bash, PowerShell o ambiente Prompt di comando.

## <a name="configuring-a-screen-lock-and-enrolling-a-fingerprint"></a>Configurazione di un blocco dello schermo e sulla registrazione di un'impronta digitale 

Per impostare un blocco dello schermo, eseguire la procedura seguente:

1. Passare a **Impostazioni > sicurezza**e selezionare **blocco schermo**:

    ![Percorso della selezione blocco schermo nella schermata di sicurezza](enrolling-fingerprint-images/testing-01.png)

2. Verrà visualizzata la schermata successiva consentirà selezionare e configurare uno dei metodi di protezione di blocco schermo: 

    ![Selezionare scorrere rapidamente, modello, il PIN o Password](enrolling-fingerprint-images/testing-02.png)

   Selezionare e completare uno dei metodi di blocco disponibile sullo schermo.

3. Dopo aver configurato il screenlock, ripristinare il **Impostazioni > sicurezza** pagina e selezionare **impronta digitale**:

    ![Percorso della selezione delle impronte digitali nella schermata di sicurezza](enrolling-fingerprint-images/testing-03.png)

4. Da qui, seguire la sequenza per aggiungere un'impronta digitale per il dispositivo:

    [![Sequenza di schermate per l'aggiunta di un'impronta digitale per il dispositivo](enrolling-fingerprint-images/testing-04-sml.png)](enrolling-fingerprint-images/testing-04.png#lightbox)

5. Nella schermata finale viene chiesto di inserire il dito sullo scanner impronta digitale: 

    ![Schermata che richiede di inserire il dito su sensore](enrolling-fingerprint-images/testing-05.png)

    Se si utilizza un dispositivo Android, è possibile completare il processo toccando un dito allo scanner. 
    
    
### <a name="simulating-a-fingerprint-scan-on-the-emulator"></a>Simulazione di un'analisi delle impronte digitali nell'emulatore

In un emulatore Android, è possibile simulare un'analisi delle impronte digitali usando il Bridge di Debug di Android. All'avvio di OS X una sessione Terminal in Windows, avviare un prompt dei comandi o una sessione di Powershell ed eseguire `adb`:

```shell
$ adb -e emu finger touch 1
```

Il valore di **1** è il _dito\_id_ per il dito "analizzato". È un tipo integer univoco assegnato per ciascuna delle impronte digitali virtuale. In futuro, quando viene eseguita l'app è possibile eseguire questa stessa ADB comando ogni volta che l'emulatore richiede per un'impronta digitale, è possibile eseguire il `adb` di comandi e passargli il _dito\_id_ per simulare l'analisi delle impronte digitali .

Una volta completata l'analisi delle impronte digitali, Android notificherà all'utente è stato aggiunto l'impronta digitale:  

![Schermata di visualizzazione delle impronte digitali aggiunta!](enrolling-fingerprint-images/testing-06.png)

## <a name="summary"></a>Riepilogo 

Questa guida viene descritto come configurare un blocco dello schermo e si registra un'impronta digitale in un dispositivo Android o in un emulatore Android. 

