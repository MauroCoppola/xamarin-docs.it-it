---
title: Programmazione supporto lingua in Xamarin
description: 'Questo documento descrive i diversi linguaggi di programmazione supportati da Xamarin. Viene descritto in c#, F #, portabile Visual Basic.NET e modelli Razor.'
ms.prod: xamarin
ms.assetid: CEE8C464-67D7-45F4-9614-EAEF5217CACC
author: asb3993
ms.author: amburns
ms.date: 02/18/2018
ms.openlocfilehash: 715f63a0be54ba3342bd63c1c76d89656313359a
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34781676"
---
# <a name="programming-language-support-in-xamarin"></a>Programmazione supporto lingua in Xamarin

## <a name="c"></a>C# 

###  <a name="async-support-overviewcross-platformplatformasyncmd"></a>[Panoramica del supporto asincrono](~/cross-platform/platform/async.md)

Versione 5 di c# introdotte due nuove parole chiave per esprimere le operazioni asincrone: async e await. Queste parole chiave consentono di scrivere codice semplice che prevede l'utilizzo di Task Parallel Library per eseguire operazioni a esecuzione prolungata (ad esempio l'accesso di rete) in un altro thread e accedere facilmente i risultati al completamento. Le versioni più recenti di xamarin. IOS e xamarin supportano async e await: questo documento vengono fornite spiegazioni e un esempio di utilizzo della nuova sintassi con Xamarin.

### <a name="c-6-language-featurescross-platformplatformcsharp-sixmd"></a>[Funzionalità del linguaggio C# 6](~/cross-platform/platform/csharp-six.md)

La versione più recente del linguaggio c#-versione 6 – continua evoluzione del linguaggio che sono meno boilerplate maggiore chiarezza e la coerenza di più. Sintassi di inizializzazione di pulizia, la possibilità di utilizzare `await` in `catch/finally` blocchi e condizionali null `?` operatore risultano particolarmente utili.

## <a name="ffsharpindexmd"></a>[F#](fsharp/index.md)

Compilazione di applicazioni mobili con F # e Xamarin.

##  <a name="portable-visual-basicnetcross-platformplatformvisual-basicindexmd"></a>[Visual Basic.NET portabile](~/cross-platform/platform/visual-basic/index.md)

Visual Studio supporta la creazione di librerie di classi portabili utilizzando Visual Basic.NET che possono quindi essere incorporati in applicazioni di Xamarin. In questo articolo viene illustrato come creare una nuova libreria di classi Portabile Visual Basic e utilizzarlo in un'applicazione di esempio xamarin. IOS, xamarin e Windows Phone.

##  <a name="building-html-views-using-razor-templatescross-platformplatformrazor-html-templatesindexmd"></a>[Viste di compilazione HTML utilizzando i modelli Razor](~/cross-platform/platform/razor-html-templates/index.md)

Xamarin consente agli sviluppatori di sfruttare il motore del modello Razor, introdotta in origine con ASP.NET MVC, insieme a c# per combinare facilmente i dati con HTML, Javascript e CSS senza la necessità di creare manualmente le stringhe HTML nel codice.
In questo articolo viene illustrato come utilizzare i modelli Razor con Xamarin per Android e iOS.
