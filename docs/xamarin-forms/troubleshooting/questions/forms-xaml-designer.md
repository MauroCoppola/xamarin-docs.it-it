---
title: Perché la finestra di progettazione XAML di Visual Studio non funziona per i file XAML di xamarin. Forms?
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: cab2eefb-c52f-4d81-866e-8f1feabbdd64
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 04/25/2017
ms.openlocfilehash: 43088beba6c6a86330cac164856be98d88f07fe2
ms.sourcegitcommit: 4f646dc5c51db975b2936169547d625c78a22b30
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34546151"
---
# <a name="why-doesnt-the-visual-studio-xaml-designer-work-for-xamarinforms-xaml-files"></a>Perché la finestra di progettazione XAML di Visual Studio non funziona per i file XAML di xamarin. Forms?

Xamarin. Forms attualmente non supporta finestre di progettazione visiva per i file XAML. Per questo motivo, quando si tenta di aprire un file XAML form in entrambi Visual Studio *finestra di progettazione dell'interfaccia utente XAML* o *finestra di progettazione dell'interfaccia utente XAML con codifica*, viene generato il messaggio di errore seguente:

> "Impossibile aprire il file con l'editor selezionato. Scegliere un altro editor."

Questa limitazione è descritta nel [Panoramica](~/xamarin-forms/xaml/xaml-basics/index.md#Overview) sezione il [nozioni di base di xamarin. Forms XAML](~/xamarin-forms/xaml/xaml-basics/index.md) Guida:

> "Non è ancora una finestra di progettazione visiva per la generazione di XAML in applicazioni di xamarin. Forms, in modo che tutte XAML deve essere scritta manualmente".

Tuttavia, l'anteprima di xamarin. Forms XAML visualizzabile selezionando il **Vista > altre finestre > Anteprima di xamarin. Forms** opzione di menu.
