---
title: Creazione di bundle per Mac App Store
description: Questo documento descrive come creare un bundle di un'app Xamarin.Mac per la pubblicazione in Mac App Store. Vengono illustrate le opzioni di firma del codice e la compilazione.
ms.prod: xamarin
ms.assetid: 00a36d7c-937d-4657-bf6a-0de9684b8f94
ms.technology: xamarin-mac
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/14/2017
ms.openlocfilehash: 3aeda97fa4a5a63d51623335c0721026b2394d2f
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34792060"
---
# <a name="bundling-for-the-mac-app-store"></a>Creazione di bundle per Mac App Store

In questa sezione vengono descritti i concetti di base per compilare con Visual Studio per Mac un'applicazione da rilasciare in Mac App Store. In base alle funzionalità aggiuntive, come ad esempio l'accesso iCloud e le notifiche push, potrebbe essere necessaria una configurazione aggiuntiva, che oltrepassa l'ambito di questo articolo.

> [!NOTE]
> Prima di iniziare questa sezione, lo sviluppatore deve aver creato un profilo di provisioning di produzione per la compilazione per Mac App Store. Per la creazione dei profili di provisioning richiesti, vedere le istruzioni riportate in precedenza nel documento.

## <a name="code-signing-options"></a>Opzioni di firma del codice

Modifica il valore di **Configurazione** su **Release** (Rilascio) prima di aggiornare le opzioni di creazione di pacchetti e firma del codice. Lo sviluppatore deve assicurarsi di usare l'**Identità** dell'azienda e il profilo di provisioning creati in precedenza quando ha firmato l'applicazione per il rilascio in App Store.

 [![Modifica delle opzioni di firma del codice](bundling-images/config02.png "Modifica delle opzioni di firma del codice")](bundling-images/config02-large.png#lightbox)

Verificare che l'opzione per creare un pacchetto di installazione sia stata selezionata nelle impostazioni **Compilazione Mac**:

[![Modifica delle opzioni di compilazione](bundling-images/config03.png "Modifica delle opzioni di compilazione")](bundling-images/config03-large.png#lightbox)

## <a name="build"></a>Compilazione

Prima della compilazione, assicurarsi che sia stata selezionata la configurazione **Release** (Rilascio). Quando lo sviluppatore compila l'app, verrà richiesto di usare entrambi i certificati:

 ![Consentire all'app di usare il certificato](bundling-images/image62.png "Consentire all'app di usare il certificato")

 ![Consentire all'app di usare il certificato](bundling-images/image63.png "Consentire all'app di usare il certificato")

Dopo aver compilato l'applicazione, lo sviluppatore può fare clic con il pulsante destro del mouse sul progetto e scegliere **Apri cartella superiore** per trovare il file del pacchetto. Nell'esempio illustrato sotto si tratta della directory `bin/x86/AppStore`.  Il file del pacchetto include un programma di installazione per l'app che può essere inviata a Apple per l'inclusione nel Mac App Store.

 ![Selezione del pacchetto di compilazione in Finder](bundling-images/image64.png "Selezione del pacchetto di compilazione in Finder")


## <a name="related-links"></a>Collegamenti correlati

- [Installazione](/visualstudio/mac/installation/)
- [Esempio Hello, Mac](~/mac/get-started/hello-mac.md)
- [Distribuire le app in Mac App Store](https://developer.apple.com/devcenter/mac/checklist/)
- [ID sviluppatore e GateKeeper](https://developer.apple.com/resources/developer-id/)
