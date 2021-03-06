---
title: Messaggi di errore Xamarin.Mac (mmp)
description: Questo documento vengono elencati gli errori generati da mmp, lo strumento utilizzato per creare il pacchetto assembly compilati in un'applicazione eseguibile Mac.
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: 5B26339F-A202-4E41-9229-D0BC9E77868E
ms.technology: xamarin-mac
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/27/2018
ms.openlocfilehash: f5cf4a9003d3fb468ffcf337c33730cb12238c44
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34792759"
---
# <a name="xamarinmac-error-messages-mmp"></a>Messaggi di errore Xamarin.Mac (mmp)

## <a name="mm0xxx-mmp-error-messages"></a>MM0xxx: i messaggi di errore mmp

Ad esempio, parametri, ambiente, strumenti mancante.

<a name="MM0000" />

#### <a name="mm0000-unexpected-error---please-file-a-bug-report-at-httpbugzillaxamarincom"></a>MM0000: Errore imprevisto - file di un bug segnalare in http://bugzilla.xamarin.com

Si è verificato un errore imprevisto. . [Un report sui bug](https://bugzilla.xamarin.com/enter_bug.cgi?product=Xamarin.Mac) con le informazioni possibili, tra cui:

* Log, di compilazione completa con massimo livello di dettaglio (ad esempio `-v -v -v -v` nella **mmp ulteriori argomenti**);
* Un test case minimo riprodurre l'errore. e
* Tutte le informazioni di versione

Il modo più semplice per ottenere informazioni sulla versione esatta consiste nell'utilizzare il **Xamarin Studio** menu **su Xamarin Studio** elemento **Mostra dettagli** pulsante e copiare e incollare la versione informazioni (è possibile utilizzare il **copia informazioni** pulsante).

<a name="MM0001" />

#### <a name="mm0001-this-version-of-xamarinmac-requires-mono-0-the-current-mono-version-is-1-please-update-the-monoframework-from-httpmono-projectcomdownloads"></a>MM0001: Questa versione di Xamarin.Mac richiede Mono {0} (la versione corrente Mono è {1}). Aggiornare il Mono.framework da http://mono-project.com/Downloads

<a name="MM0003" />

#### <a name="mm0003-application-name-0exe-conflicts-with-an-sdk-or-product-assembly-dll-name"></a>MM0003: Nome dell'applicazione '{0}.exe' è in conflitto con un nome di assembly (DLL) SDK o prodotto.

<a name="MM0007" />

#### <a name="mm0007-the-root-assembly-0-does-not-exist"></a>MM0007: L'assembly radice '{0}' non esiste

<a name="MM0008" />

#### <a name="mm0008-you-should-provide-one-root-assembly-only-found-0-assemblies-1"></a>MM0008: È necessario fornire un unico assembly radice solo, trovati {0} assembly: '{1}'

<a name="MM0010" />

#### <a name="mm0010-could-not-parse-the-command-line-arguments-0"></a>MM0010: Non è riuscito ad analizzare gli argomenti della riga di comando: {0}

<!-- 0013 is unused -->

<a name="MM0016" />

#### <a name="mm0016-the-option-0-has-been-deprecated"></a>MM0016: L'opzione '{0}' è stato deprecato.

<a name="MM0017" />

#### <a name="mm0017-you-should-provide-a-root-assembly"></a>MM0017: È necessario fornire un assembly radice

<a name="MM0018" />

#### <a name="mm0018-unknown-command-line-argument-0"></a>MM0018: Argomento della riga di comando sconosciuto: '{0}'

<a name="MM0020" />

#### <a name="mm0020-the-valid-options-for-0-are-1"></a>MM0020: Le opzioni valide per '{0}'sono'{1}'.

<a name="MM0023" />

#### <a name="mm0023-application-name-0exe-conflicts-with-another-user-assembly"></a>MM0023: Nome dell'applicazione '{0}.exe' è in conflitto con un altro assembly utente.

<a name="MM0026" />

#### <a name="mm0026-could-not-parse-the-command-line-argument-0-1"></a>MM0026: Non è stato possibile analizzare l'argomento della riga di comando '{0}': {1}

<a name="MM0043" />

#### <a name="mm0043-the-boehm-garbage-collector-is-not-supported-the-sgen-garbage-collector-has-been-selected-instead"></a>MM0043: Boehm garbage collector non è supportato. SGen garbage collector è stato selezionato.

<a name="MM0050" />

#### <a name="mm0050-you-cannot-provide-a-root-assembly-if---no-root-assembly-is-passed"></a>MM0050: Non è possibile fornire un assembly radice se - no-radice-assembly viene passato.

<a name="MM0051" />

#### <a name="mm0051-an-output-directory---output-is-required-if---no-root-assembly-is-passed"></a>MM0051: Una directory di output (-output) è obbligatorio se - no-radice-assembly viene passato.

<a name="MM0053" />

#### <a name="mm0053-cannot-disable-new-refcount-with-the-unified-api"></a>MM0053: Non è possibile disabilitare il nuovo conteggio dei riferimenti con un'API unificata.

<a name="MM0056" />

#### <a name="mm0056-cannot-find-xcode-in-any-of-our-default-locations-please-install-xcode-or-pass-a-custom-path-using---sdkrootpath"></a>MM0056: Impossibile trovare Xcode in uno dei nostri percorsi predefiniti. Installare Xcode, o passare un percorso personalizzato usando - sdkroot =<path>

<a name="MM0059" />

#### <a name="mm0059-could-not-find-the-currently-selected-xcode-on-the-system-0"></a>MM0059: Non è riuscito a trovare Xcode attualmente selezionato nel sistema: {0};

<a name="MM0060" />

#### <a name="mm0060-could-not-find-the-currently-selected-xcode-on-the-system-xcode-select---print-path-returned-0-but-that-directory-does-not-exist"></a>MM0060: Impossibile trovare il Xcode attualmente selezionato nel sistema. 'xcode-selezionare-print-path' ha restituito '{0}', ma tale directory non esiste.

<a name="MM0068" />

#### <a name="mm0068-invalid-value-for-target-framework-0"></a>MM0068: Valore non valido per il framework di destinazione: {0}.

<a name="MM0071" />

#### <a name="mm0071-unknown-platform--this-usually-indicates-a-bug-in-xamarinmac-please-file-a-bug-report-at-httpsbugzillaxamarincom-with-a-test-case"></a>MM0071: Piattaforma sconosciuta: *. Ciò indica in genere un bug in Xamarin.Mac; inviare una segnalazione di bug in https://bugzilla.xamarin.com con un test case.

Ciò indica in genere un bug in Xamarin.Mac; inviare una segnalazione di bug in [ https://bugzilla.xamarin.com ](https://bugzilla.xamarin.com/enter_bug.cgi?product=Xamarin.Mac) con un test case.

<a name="MM0079" />

#### <a name="mm0079-internal-error---no-executable-was-copied-into-the-app-bundle-please-contact-supportxamarincom"></a>MM0079: Errore interno - alcun eseguibile è stato copiato in bundle dell'app. Contattare 'support@xamarin.com'

<a name="MM0080" />

#### <a name="mm0080-disabling-newrefcount---new-refcountfalse-is-deprecated"></a>MM0080: Disabilitazione NewRefCount, --new-refcount:false, è deprecata.

<!-- 0088 used by mtouch -->
<!-- 0089 used by mtouch -->

<a name="MM0091" />

#### <a name="mm0091-this-version-of-xamarinmac-requires-the--sdk-shipped-with-xcode--either-upgrade-xcode-to-get-the-required-header-files-or-use-the-dynamic-registrar-or-set-the-managed-linker-behaviour-to-link-platform-or-link-framework-sdks-only-to-try-to-avoid-the-new-apis"></a>MM0091: Questa versione di Xamarin.Mac richiede la * SDK (fornita con Xcode *). L'aggiornamento Xcode per ottenere i file di intestazione obbligatori o utilizzare il programma di registrazione dinamica o impostare il comportamento del linker gestito per piattaforma di collegamento o solo collegamento Framework SDK (per tentare di evitare le nuove API).

Xamarin.Mac richiede i file di intestazione, dalla versione di SDK specificato nel messaggio di errore, per compilare l'applicazione con il registrar statico. Il metodo consigliato per correggere l'errore consiste nell'aggiornare Xcode per ottenere il SDK necessario, si includerà tutti i file di intestazione necessari. Se si dispone di più versioni di Xcode installato o si desidera utilizzare un Xcode in un percorso non predefinito, assicurarsi di impostare il percorso corretto Xcode nelle preferenze dell'IDE.

Una soluzione alternativa potenziale è consentire al linker gestito. Questa operazione rimuoverà inutilizzati API incluso, la maggior parte dei casi, la nuova API in cui i file di intestazione sono mancanti (o incompleti). Tuttavia non funzionerà se il progetto usa API che è stato introdotto in un SDK più recente di quella del Xcode fornisce.

Una soluzione alternativa potenziale in secondo luogo, è utilizzare il programma di registrazione dinamica. Questo verrà impone un costo di avvio di registrazione in modo dinamico dei tipi ma rimuovere il requisito di file di intestazione. 

Una soluzione ultimo riconosciuti potrebbe consistere nell'utilizzare una versione precedente di Xamarin.Mac, uno che supporti il SDK del progetto è necessario.

<a name="MM0097" />

#### <a name="mm0097-machineconfig-file-0-can-not-be-found"></a>MM0097: file Machine. config '{0}' non può essere trovato.

<a name="MM0098" />

#### <a name="mm0098-aot-compilation-is-only-available-on-unified"></a>MM0098: Compilazione AOT è disponibile solo in unificata

<a name="MM0099" />

#### <a name="mm0099-internal-error-0-please-file-a-bug-report-with-a-test-case-httpbugzillaxamarincom"></a>MM0099: Errore interno {0}. Inviare una segnalazione di bug con un test case (http://bugzilla.xamarin.com).

<a name="MM0114" />

#### <a name="mm0114-hybrid-aot-compilation-requires-all-assemblies-to-be-aot-compiled"></a>MM0114: Ibrida AOT compilazione richiede tutti gli assembly da AOT compilati.

## <a name="mm1xxx-file-copy--symlinks-project-related"></a>MM1xxx: copia del file / collegamenti simbolici (progetto correlato)

<a name="MM1034" />

#### <a name="mm1034-could-not-create-symlink-file---target-error-number"></a>MM1034: Non è riuscito a creare symlink '{file}' -> '{target}': errore {numero}

### <a name="mm14xx-product-assemblies"></a>MM14xx: Set di prodotti

<a name="MM1401" />

#### <a name="mm1401-the-required-0-assembly-is-missing-from-the-references"></a>MM1401: Richiesto '{0}' assembly mancante dai riferimenti

<a name="MM1402" />

#### <a name="mm1402-the-assembly-0-is-not-compatible-with-this-tool"></a>MM1402: L'assembly '{0}' non è compatibile con questo strumento

<a name="MM1403" />

#### <a name="mm1403-0-1-could-not-be-found-target-framework-0-is-unusable-to-package-the-application"></a>MM1403: {0} '{1}' non è stato trovato. Framework di destinazione '{0}' non è utilizzabile per il pacchetto dell'applicazione.

<a name="MM1404" />

#### <a name="mm1404-target-framework-0-is-invalid"></a>MM1404: Framework di destinazione '{0}' non è valido.

<a name="MM1405" />

#### <a name="mm1405-usefullxammacframework-must-always-target-framework-net-45-not-0-which-is-invalid"></a>MM1405: useFullXamMacFramework deve sempre avere come destinazione framework .NET 4.5, non '{0}' che non è valido

<a name="MM1406" />

#### <a name="mm1406-target-framework-0-is-invalid-when-targetting-xamarinmac-45-net-framwork"></a>MM1406: Framework di destinazione '{0}' non è valido quando destinata Xamarin.Mac 4.5 .NET Framework.

<a name="MM1407" />

#### <a name="mm1407-mismatch-between-xamarinmac-reference-0-and-target-framework-selected-1"></a>MM1407: Mancata corrispondenza tra Xamarin.Mac riferimento '{0}'e il framework di destinazione selezionato'{1}'.

### <a name="mm15xx-assembly-gathering-not-requiring-linker-errors"></a>MM15xx: Errori Assembly raccolta (che non richiedono del linker)

<a name="MM1501" />

#### <a name="mm1501-can-not-resolve-reference-0"></a>MM1501: Può risolvere il riferimento: {0}

### <a name="machocs"></a>MachO.cs

<a name="MM1600" />

#### <a name="mm1600-not-a-mach-o-dynamic-library-unknown-header-0x0-1"></a>MM1600: Non una O uguale alla libreria dinamica (intestazione sconosciuta ' 0 x{0}'): {1}.

<a name="MM1601" />

#### <a name="mm1601-not-a-static-library-unknown-header-0-1"></a>MM1601: Non una libreria statica (intestazione sconosciuta '{0}'): {1}.

<a name="MM1602" />

#### <a name="mm1602-not-a-mach-o-dynamic-library-unknown-header-0x0-1"></a>MM1602: Non una O uguale alla libreria dinamica (intestazione sconosciuta ' 0 x{0}'): {1}.

<a name="MM1603" />

#### <a name="mm1603-unknown-format-for-fat-entry-at-position-0-in-1"></a>MM1603: Formato sconosciuto per la voce fat nella posizione {0} in {1}.

<a name="MM1604" />

#### <a name="mm1604-file-of-type-0-is-not-a-macho-file-1"></a>MM1604: File di tipo {0} non è un file MachO ({1}).

## <a name="mm2xxx-linker"></a>MM2xxx: Linker

### <a name="mm20xx-linker-general-errors"></a>MM20xx: Gli errori del Linker (generale)

<a name="MM2001" />

#### <a name="mm2001-could-not-link-assemblies"></a>MM2001: Non è possibile collegare gli assembly

<a name="MM2002" />

#### <a name="mm2002-can-not-resolve-reference-0"></a>MM2002: Può risolvere il riferimento: {0}

<a name="MM2003" />

#### <a name="mm2003-option-0-will-be-ignored-since-linking-is-disabled"></a>MM2003: Opzione '{0}' verrà ignorato perché il collegamento è disabilitato

<a name="MM2004" />

#### <a name="mm2004-extra-linker-definitions-file-0-could-not-be-located"></a>MM2004: File di definizione del linker Extra '{0}' non è stato trovato.

<a name="MM2005" />

#### <a name="mm2005-definitions-from-0-could-not-be-parsed"></a>MM2005: Le definizioni da '{0}' non è stato possibile analizzare.

<a name="MM2006" />

#### <a name="mm2006-native-library-0-was-referenced-but-could-not-be-found"></a>MM2006: La libreria nativa '{0}' viene fatto riferimento ma non è stato trovato.

<a name="MM2007" />

#### <a name="mm2007-xamarinmac-unified-api-against-a-full-net-profile-does-not-support-linking-pass-the--nolink-flag"></a>MM2007: Xamarin.Mac Unified API rispetto a un profilo completo di .NET non supporta il collegamento. Passare il flag - nolink.

<a name="MM2009" />

#### <a name="mm2009-referenced-by-01------this-message-is-related-to-mm2006-"></a>: MM2009 Fa riferimento {0}.{1}     ** Questo messaggio è correlato a MM2006 **

<a name="MM2010" />

#### <a name="mm2010-unknown-httpmessagehandler-0-valid-values-are-httpclienthandler-default-cfnetworkhandler-or-nsurlsessionhandler"></a>MM2010: HttpMessageHandler sconosciuto `{0}`. I valori validi sono HttpClientHandler (impostazione predefinita), CFNetworkHandler o NSUrlSessionHandler

<a name="MM2011" />

#### <a name="mm2011-unknown-tlsprovider-0--valid-values-are-default-or-appletls"></a>MM2011: TLSProvider sconosciuto '{0}.  I valori validi sono default o appletls

<a name="MM2012" />

#### <a name="mm2012-only-first-0-of-1-referenced-by-warnings-shown--this-message-related-to-2009-"></a>MM2012: Solo le prime {0} di {1} "Fa riferimento" avvisi visualizzati. ** Questo messaggio correlato a 2009 \*\*

<a name="MM2013" />

#### <a name="mm2013-failed-to-resolve-the-reference-to-0-referenced-in-1-the-app-will-not-include-the-referenced-assembly-and-may-fail-at-runtime"></a>MM2013: Non è stato possibile risolvere il riferimento a "{0}", cui viene fatto riferimento in"{1}". L'app non includerà l'assembly di riferimento e potrebbe non riuscire in fase di esecuzione.

<a name="MM2014" />

#### <a name="mm2014-xamarinmac-extensions-do-not-support-linking-request-for-linking-will-be-ignored--this-message-is-obsolete-in-xm-36-"></a>MM2014: Estensioni Xamarin.Mac non supportano il collegamento. La richiesta di collegamento verrà ignorato. ** Questo messaggio è obsoleto in XM 3.6 + \*\*

<!-- 2015 used by mtouch -->

<a name="MM2016" />

#### <a name="mm2016-invalid-tlsprovider-0-option-the-only-valid-value-1-will-be-used"></a>MM2016: Non valido TlsProvider `{0}` opzione. L'unico valore valido `{1}` verrà utilizzato.

<a name="MM2017" />

#### <a name="mm2017-could-not-process-xml-description-0"></a>MM2017: Non è riuscito a elaborare descrizione XML: {0}

<a name="MM202x" />

#### <a name="mm202x-binding-optimizer-failed-processing-"></a>MM202x: Query Optimizer di associazione non è riuscita l'elaborazione `...`.

<a name="MM2100" />

#### <a name="mm2100-xamarinmac-classic-api-does-not-support-platform-linking"></a>MM2100: Xamarin.Mac classica API non supporta il collegamento della piattaforma.

<a name="MM2103" />

#### <a name="mm2103-error-processing-assembly--"></a>MM2103: Errore durante l'elaborazione dell'assembly '\*': *

Si è verificato un errore imprevisto durante l'elaborazione di un assembly.

L'assembly che causa il problema è denominato nel messaggio di errore. Per risolvere il problema dell'assembly dovrà essere specificato in un [rapporto bug](https://bugzilla.xamarin.com) insieme a un log di compilazione completa con livello di dettaglio abilitato (ad esempio `-v -v -v -v` nel **mtouch ulteriori argomenti**).

<a name="MM2104" />

#### <a name="mm2104-unable-to-link-assembly-0-as-it-is-mixed-mode"></a>MM2104: Non è possibile collegare assembly '{0}' perché è in modalità mista.

Assembly in modalità mista non possono essere elaborate dal linker.

Vedere https://msdn.microsoft.com/library/x0w2664k.aspx per ulteriori informazioni sull'assembly in modalità mista.

## <a name="mm3xxx-aot"></a>MM3xxx: AOT

### <a name="mm30xx-aot-general-errors"></a>MM30xx: Errori AOT (generale)

<a name="MM3001" />

#### <a name="mm3001-could-not-aot-the-assembly-0"></a>MM3001: Impossibile AOT non l'assembly '{0}'

<!-- 3002 used by mtouch -->
<!-- 3003 used by mtouch -->
<!-- 3004 used by mtouch -->
<!-- 3005 used by mtouch -->
<!-- 3006 used by mtouch -->
<!-- 3007 used by mtouch -->
<!-- 3008 used by mtouch -->

<a name="MM3009" />

#### <a name="mm3009-aot-of-0-was-requested-but-was-not-found"></a>MM3009: AOT di '{0}' è stato richiesto ma non è stato trovato

<a name="MM3010" />

#### <a name="mm3010-exclusion-of-aot-of-0-was-requested-but-was-not-found"></a>MM3010: Esclusione di AOT di '{0}' è stato richiesto ma non è stato trovato

## <a name="mm4xxx-code-generation"></a>MM4xxx: generazione del codice

### <a name="mm40xx-driverm"></a>MM40xx: driver.m

<a name="MM4001" />

#### <a name="mm4001-the-main-template-could-not-be-expanded-to-0"></a>MM4001: Il modello principale potrebbe non essere espanso fino a `{0}`.

### <a name="mm41xx-registrar"></a>MM41xx: registrar

<a name="MM4134" />

#### <a name="mm4134-your-application-is-using-the-0-framework-which-isnt-included-in-the-macos-sdk-youre-using-to-build-your-app-this-framework-was-introduced-in-osx-2-while-youre-building-with-the-macos-1-sdk-this-configuration-is-not-supported-with-the-static-registrar-pass---registrardynamic-as-an-additional-mmp-argument-in-your-projects-mac-build-option-to-select-alternatively-select-a-newer-sdk-in-your-apps-mac-build-options"></a>MM4134: L'applicazione usi il '{0}' framework, che non è incluso nel SDK MacOS in uso per compilare l'app (questo framework è stato introdotto in OSX {2}, mentre si vogliano compilare con il MacOS {1} SDK.) Questa configurazione non è supportata con il programma di registrazione statico (pass - registrar: dinamico come argomento mmp aggiuntiva nell'opzione di compilazione Mac del progetto per selezionare). In alternativa selezionare un SDK più recente nelle opzioni di compilazione Mac dell'app.

## <a name="mm5xxx-gcc-and-toolchain"></a>MM5xxx: GCC e toolchain

### <a name="mm51xx-compilation"></a>MM51xx: compilazione

<a name="MM5101" />

#### <a name="mm5101-missing-0-compiler-please-install-xcode-command-line-tools-component"></a>MM5101: Manca '{0}' compilatore. Installare il componente 'Strumenti da riga di comando' Xcode.

<!-- 5102 used by mtouch -->

<a name="MM5103" />

#### <a name="mm5103-failed-to-compile-error-code---0-please-file-a-bug-report-at-httpbugzillaxamarincom"></a>MM5103: Impossibile compilare. Codice di errore - {0}. Inviare una segnalazione di bug in http://bugzilla.xamarin.com

<!-- 5104 used by mtouch -->

### <a name="mm52xx-linking"></a>MM52xx: il collegamento

<a name="MM5202" />

#### <a name="mm5202-monoframework-mdk-is-missing-please-install-the-mdk-for-your-monoframework-version-from-httpmono-projectcomdownloads"></a>MM5202: Mono.framework MDK mancante. Installare MDK per la versione Mono.framework da http://mono-project.com/Downloads

<a name="MM5203" />

#### <a name="mm5203-cant-find-libxammaca-likely-because-of-a-corrupted-xamarinmac-installation-please-reinstall-xamarinmac"></a>MM5203: Impossibile trovare libxammac.a, probabilmente a causa di un'installazione Xamarin.Mac danneggiata. Reinstallare Xamarin.Mac.

<a name="MM5204" />

#### <a name="mm5204-invalid-architecture-x8664-is-only-supported-on-non-classic-profiles"></a>MM5204: Architettura non valido. X86_64 è supportata solo nei profili non classico.

<a name="MM5205" />

#### <a name="mm5205-invalid-architecture-0-valid-architectures-are-i386-and-x8664-when---profilemobile"></a>MM5205: Architettura non valido '{0}'. Le architetture valide sono i386 e x86_64 (quando - profilo = mobile).

<a name="MM5218" />

#### <a name="mm5218-cant-ignore-the-dynamic-symbol-symbol---ignore-dynamic-symbolsymbol-because-it-was-not-detected-as-a-dynamic-symbol"></a>MM5218: Non è possibile ignorare dinamico {simbolo} (-simbolo dinamico ignorare = {simbolo}) perché non è stato rilevato come simbolo di dinamico.

Vedere la [mtouch equivalente avviso](~/ios/troubleshooting/mtouch-errors.md#MT5218).

<!-- 5206 used by mtouch -->
<!-- 5207 used by mtouch -->
<!-- 5208 used by mtouch -->
<!-- 5209 used by mtouch -->
<!-- 5210 used by mtouch -->
<!-- 5211 used by mtouch -->
<!-- 5212 used by mtouch -->
<!-- 5213 used by mtouch -->
<!-- 5214 used by mtouch -->
<!-- 5215 used by mtouch -->
<!-- 5216 used by mtouch -->
<!-- 5217 used by mtouch -->

### <a name="mm53xx-other-tools"></a>MM53xx: altri strumenti

<a name="MM5301" />

#### <a name="mm5301-pkg-config-could-not-be-found-please-install-the-monoframework-from-httpmono-projectcomdownloads"></a>MM5301: pkg-config non trovato. Installare Mono.framework da http://mono-project.com/Downloads

<!-- 5302 used by mtouch -->
<!-- 5303 used by mtouch -->
<!-- 5304 used by mtouch -->

<a name="MM5305" />

#### <a name="mm5305-missing-otool-tool-please-install-xcode-command-line-tools-component"></a>MM5305: Manca 'otool' strumento. Installare il componente 'Strumenti da riga di comando' Xcode

<a name="MM5306" />

#### <a name="mm5306-missing-dependencies-please-install-xcode-command-line-tools-component"></a>MM5306: Dipendenze mancanti. Installare il componente 'Strumenti da riga di comando' Xcode

<a name="MM5308" />

#### <a name="mm5308-xcode-license-agreement-may-not-have-been-accepted--please-launch-xcode"></a>MM5308: Contratto di licenza Xcode potrebbe non sono stata accettata.  Avviare Xcode.

<a name="MM5309" />

#### <a name="mm5309-native-linking-failed-with-error-code-1--check-build-log-for-details"></a>MM5309: Collegamento nativo non riuscito con codice di errore 1.  Vedere il log di compilazione per i dettagli.

<a name="MM5310" />

#### <a name="mm5310-installnametool-failed-with-an-error-code-0-check-build-log-for-details"></a>MM5310: install_name_tool non riuscita con codice errore '{0}'. Vedere il log di compilazione per i dettagli.

<!-- MM6xxx: mmp internal tools -->
<!-- MM7xxx: reserved -->

## <a name="mm8xxx-runtime"></a>MM8xxx: runtime

### <a name="mm800x-misc"></a>MM800x: varie

<!-- 8000 used by mtouch -->
<!-- 8001 used by mtouch -->
<!-- 8002 used by mtouch -->
<!-- 8003 used by mtouch -->
<!-- 8004 used by mtouch -->
<!-- 8005 used by mtouch -->
<!-- 8006 used by mtouch -->
<!-- 8007 used by mtouch -->
<!-- 8008 used by mtouch -->
<!-- 8009 used by mtouch -->
<!-- 8010 used by mtouch -->
<!-- 8011 used by mtouch -->
<!-- 8012 used by mtouch -->
<!-- 8013 used by mtouch -->
<!-- 8014 used by mtouch -->
<!-- 8015 used by mtouch -->
<!-- 8016 used by mtouch -->

<a name="MM8017" />

#### <a name="mm8017-the-boehm-garbage-collector-is-not-supported-please-use-sgen-instead"></a>MM8017: Boehm garbage collector non è supportato. Usare SGen.

