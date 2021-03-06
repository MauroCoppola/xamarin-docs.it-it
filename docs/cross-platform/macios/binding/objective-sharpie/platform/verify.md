---
title: Obiettivo Sharpie verificare gli attributi
description: Questo documento descrive l'attributo [Verify] generato da Sharpie obiettivo. L'attributo [Verify] vengono evidenziate per gli sviluppatori in cui è necessario verificare manualmente output dell'obiettivo Sharpie.
ms.prod: xamarin
ms.assetid: 107FBCEA-266B-4295-B7AA-40A881B82B7B
author: asb3993
ms.author: amburns
ms.date: 01/15/2016
ms.openlocfilehash: 4bca896afb4dfc96fd6c1d7cdf489feb6a879e31
ms.sourcegitcommit: ec50c626613f2f9af51a9f4a52781129bcbf3fcb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2018
ms.locfileid: "37855029"
---
# <a name="objective-sharpie-verify-attributes"></a>Obiettivo Sharpie verificare gli attributi

Si potrà spesso notare che associazioni prodotte da Sharpie obiettivo verranno annotate con il `[Verify]` attributo. Questi attributi indicano che occorre _verificare_ che obiettivo Sharpie ha l'aspetto corretto confrontando l'associazione con la dichiarazione di C/Objective-C originale (che verrà fornita in un commento sopra la dichiarazione di associazione).

Verifica è consigliata per _tutti i_ associato dichiarazioni, ma è più probabile _obbligatorio_ per le dichiarazioni annotati con il `[Verify]` attributo. Questo avviene perché in molte situazioni, non è sufficiente metadati nel codice sorgente nativa originale per dedurre come meglio produrre un'associazione. Potrebbe essere necessario fare riferimento a documentazione o commenti del codice all'interno di file di intestazione per rendere il processo decisionale dell'associazione.

Dopo avere verificato che il binding è correggere o sono corretti in modo che sia corretto, _rimuovere_ il `[Verify]` attributo dall'associazione.

> [!IMPORTANT]
> `[Verify]` gli attributi causano intenzionalmente errori di compilazione di c# in modo che si sono obbligati a verificare l'associazione. È necessario rimuovere il `[Verify]` attributo dopo avere esaminato (e possibilmente corretti) nel codice.

## <a name="verify-hints-reference"></a>Verificare il riferimento di hint

L'argomento hint fornito per l'attributo può essere tra cui viene fatto riferimento con documentazione riportate di seguito. Documentazione per qualsiasi prodotto `[Verify]` attributi verranno forniti nella console anche dopo l'associazione è stata completata.

|`[Verify]` Hint|Descrizione|
|---|---|
|InferredFromPreceedingTypedef|Il nome di questa dichiarazione è stata dedotta per convenzione comune dall'immediatamente precedente `typedef` nel codice sorgente nativo originale. Verificare che il nome derivato sia corretto perché questa convenzione è ambigua.|
|ConstantsInterfaceAssociation|Non è possibile piuttosto complesso per determinare con quale interfaccia Objective-C può essere associata una dichiarazione di variabile extern. Le istanze di questi vengono associate come `[Field]` proprietà in un'interfaccia parziale in un'interfaccia concreta quasi-by per produrre un'API più intuitiva, possibilmente eliminando le 'costanti' interfaccia completamente.|
|MethodToProperty|Un metodo di Objective-C è stato associato come proprietà c# a causa di convenzione, ad esempio che non accettano parametri e restituire un valore (restituito non void). Spesso i metodi simili ai seguenti devono essere associati come proprietà a un'API coloro, della superficie di attacco, ma a volte possono verificarsi falsi positivi e l'associazione deve essere effettivamente un metodo.|
|StronglyTypedNSArray|Nativo `NSArray*` associati come `NSObject[]`. È possibile digitare più fortemente la matrice nell'associazione basata sulla previsione impostato tramite la documentazione dell'API (ad esempio, i commenti nel file di intestazione) oppure esaminando il contenuto della matrice tramite test. Ad esempio, un NSArray * che contiene solo NSNumber * instancescan essere associato come `NSNumber[]` invece di `NSObject[]`.|

È possibile ricevere rapidamente documentazione per l'uso un hint di `sharpie verify-docs` dello strumento, ad esempio:

```csharp
sharpie verify-docs InferredFromPreceedingTypedef
```

## <a name="related-links"></a>Collegamenti correlati

- [Corso di Xamarin University: Creazione di una libreria di binding di Objective-C](https://university.xamarin.com/classes/track/all#building-an-objective-c-bindings-library)
- [Corsi di Xamarin University: Compilare una libreria di binding Objective-C con Sharpie obiettivo](https://university.xamarin.com/classes/track/all#build-an-objective-c-bindings-library-with-objective-sharpie)
