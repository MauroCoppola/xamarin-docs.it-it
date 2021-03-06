---
title: Installazione di Xamarin.iOS in Windows
description: Questo documento descrive come configurare un computer Windows, configurare un host di compilazione Mac e associare Windows al Mac per lo sviluppo di Xamarin.iOS.
ms.prod: xamarin
ms.assetid: abf85d3e-a365-44a2-b1a4-6c572c7f76dd
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 04/16/2018
ms.openlocfilehash: 2bff37aba9b961b7308bf261377951dc96bd8e34
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34786064"
---
# <a name="installing-xamarinios-on-windows"></a>Installazione di Xamarin.iOS in Windows

_Questo articolo descrive come configurare un computer Windows e un host di compilazione Mac per lo sviluppo con Xamarin.iOS._

## <a name="overview"></a>Panoramica

Per compilare le app Xamarin.iOS con Visual Studio 2017 in Windows, è necessario quanto segue:
 
-  Un computer Windows con Visual Studio 2017 installato. Può trattarsi di un computer fisico o di una macchina virtuale.
    - [Requisiti di sistema Windows](~/cross-platform/get-started/requirements.md#windows-requirements)
    
-  Un Mac accessibile dalla rete configurato con strumenti di compilazione Apple e Xamarin.iOS. Visual Studio 2017 accede a questa macchina tramite una connessione di rete per usare gli strumenti di compilazione Apple, necessari per la compilazione di applicazioni iOS native. 
    - [Requisiti di sistema Mac](~/cross-platform/get-started/requirements.md#macos-requirements)

## <a name="setup"></a>Configurazione

Per predisporre la configurazione per lo sviluppo con Xamarin.iOS in Visual Studio 2017, seguire questi passaggi:

1. Configurare Windows (Installare Visual Studio 2017)

    Xamarin.iOS può essere usato con Visual Studio 2017 Community, Professional ed Enterprise Edition, in un computer autonomo o una macchina virtuale.
    
    - [Installare Visual Studio 2017](~/cross-platform/get-started/installation/windows.md).

2. Configurare il Mac (Installare Xcode e Visual Studio per Mac)

    Per compilare, eseguire il debug e firmare le applicazioni iOS per la distribuzione, Visual Studio 2017 deve avere accesso tramite rete a un host di compilazione Mac configurato con gli strumenti di sviluppo Apple (Xcode) e Xamarin.iOS.

    - [Scaricare e installare Xcode da Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). 
    - [Installare Visual Studio per Mac](https://docs.microsoft.com/visualstudio/mac/installation), che installa anche Xamarin.iOS.

    > [!NOTE] 
    > Se si preferisce non installare Visual Studio per Mac, a partire da [Visual Studio 2017 versione 15.6](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#automatic-macos-provisioning) Visual Studio 2017 può configurare automaticamente l'host di compilazione Mac con il software necessario per compilare applicazioni Xamarin.iOS. Per altre informazioni, vedere [Provisioning automatico del Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md#automatic-mac-provisioning).

3. Eseguire l'associazione al Mac (Connettere Visual Studio 2017 al Mac)

    Per fare in modo che Visual Studio 2017 usi gli strumenti di compilazione iOS nel Mac, i due computer devono essere connessi in rete.

    - [Leggere la guida Associazione al Mac](~/ios/get-started/installation/windows/connecting-to-mac/index.md).

## <a name="summary"></a>Riepilogo

Questo articolo descrive come configurare un computer Windows e l'host di compilazione Mac associato per lo sviluppo con Xamarin.iOS.

## <a name="next-steps"></a>Passaggi successivi

- [Introduzione a Xamarin.iOS per Visual Studio](introduction-to-xamarin-ios-for-visual-studio.md)
- [Configurazione di Visual Studio 2017](config-options.md)
- [Provisioning dei dispositivi](~/ios/get-started/installation/device-provisioning/index.md)
