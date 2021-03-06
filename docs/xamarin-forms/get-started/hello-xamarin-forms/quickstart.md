---
title: Guida introduttiva di Xamarin.Forms
description: Questo articolo spiega come creare un'applicazione che converte un numero di telefono alfanumerico immesso dall'utente in un numero di telefono numerico e lo chiama.
ms.topic: quickstart
ms.prod: xamarin
ms.assetid: 3f2f9c2d-d204-43bc-8c8a-a55ce1e6d2c8
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 06/13/2018
ms.openlocfilehash: 7399cab611b726eb7bb72928f504086fb842fb74
ms.sourcegitcommit: b56b3f906d2c05a3f1be219ef41be8b79e519b8e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39242433"
---
# <a name="xamarinforms-quickstart"></a>Guida introduttiva di Xamarin.Forms

Questa procedura dettagliata illustra come creare un'applicazione che converte un numero di telefono alfanumerico immesso dall'utente in un numero di telefono numerico e lo chiama. Il risultato è riportato di seguito:

[![](quickstart-images/intro-app-examples-sml.png "Applicazione Phoneword")](quickstart-images/intro-app-examples.png#lightbox "Applicazione Phoneword")

Creare l'applicazione Phoneword come indicato di seguito:

# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

1. Nella schermata **Start**, avviare Visual Studio. Verrà aperta la pagina iniziale:

    ![](quickstart-images/vs/start-page.png "Visual Studio")

2. In Visual Studio fare clic su **Crea nuovo progetto...** per creare un nuovo progetto:

    ![](quickstart-images/vs/new-solution.png "Nuovo progetto")

3. Nella finestra di dialogo **Nuovo progetto** fare clic su **Multipiattaforma**, selezionare il modello **App per dispositivi mobili (Xamarin.Forms)**, impostare il Nome su **Phoneword**, scegliere un percorso adatto per il progetto e fare clic sul pulsante **OK**:

    ![](quickstart-images/vs/new-project.w157.png "Modelli di progetto multipiattaforma")

    > [!NOTE]
    > La mancata denominazione della soluzione **Phoneword** comporterà numerosi errori di compilazione.

4. Nella finestra di dialogo **Nuova app multipiattaforma** fare clic su **App vuota**, selezionare **.NET Standard** come strategia di condivisione del codice e fare clic sul pulsante **OK**:

    ![](quickstart-images/vs/new-app.png "Nuova app multipiattaforma")

5. Fare doppio clic su **MainPage.xaml** nel progetto **Phoneword** in **Esplora soluzioni** per aprire il file:

    ![](quickstart-images/vs/open-mainpage-xaml.png "Aprire MainPage.xaml")

6. In **MainPage.xaml** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice definisce in modo dichiarativo l'interfaccia utente per la pagina:

    ```xaml
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                       x:Class="Phoneword.MainPage">
        <ContentPage.Padding>
            <OnPlatform x:TypeArguments="Thickness">
                <On Platform="iOS" Value="20, 40, 20, 20" />
                <On Platform="Android, UWP" Value="20" />
            </OnPlatform>
        </ContentPage.Padding>
        <StackLayout>
          <Label Text="Enter a Phoneword:" />
          <Entry x:Name="phoneNumberText" Text="1-855-XAMARIN" />
          <Button x:Name="translateButon" Text="Translate" Clicked="OnTranslate" />
          <Button x:Name="callButton" Text="Call" IsEnabled="false" Clicked="OnCall" />
        </StackLayout>
    </ContentPage>
    ```

    Salvare le modifiche apportate a **MainPage.xaml** premendo **CTRL+S** e chiudere il file.

7. In **Esplora soluzioni** espandere **MainPage.xaml** e fare doppio clic su **MainPage.xaml.cs** per aprirlo:

    ![](quickstart-images/vs/open-mainpage-codebehind.png "Aprire MainPage.xaml.cs")

8. In **MainPage.xaml.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. I metodi `OnTranslate` e `OnCall` verranno eseguiti in risposta alla selezione dei pulsanti di **traduzione** e **chiamata** nell'interfaccia utente, rispettivamente:

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace Phoneword
    {
        public partial class MainPage : ContentPage
        {
            string translatedNumber;

            public MainPage ()
            {
                InitializeComponent ();
            }

            void OnTranslate (object sender, EventArgs e)
            {
                translatedNumber = PhonewordTranslator.ToNumber (phoneNumberText.Text);
                if (!string.IsNullOrWhiteSpace (translatedNumber)) {
                    callButton.IsEnabled = true;
                    callButton.Text = "Call " + translatedNumber;
                } else {
                    callButton.IsEnabled = false;
                    callButton.Text = "Call";
                }
            }

            async void OnCall (object sender, EventArgs e)
            {
                if (await this.DisplayAlert (
                        "Dial a Number",
                        "Would you like to call " + translatedNumber + "?",
                        "Yes",
                        "No")) {
                    var dialer = DependencyService.Get<IDialer> ();
                    if (dialer != null)
                        dialer.Dial (translatedNumber);
                }
            }
        }
    }
    ```

    > [!NOTE]
    > Se si prova a compilare l'applicazione a questo punto, si verificano errori che verranno risolti in un secondo momento.

    Salvare le modifiche apportate a **MainPage.xaml.cs** premendo **CTRL+S** e chiudere il file.

9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Phoneword** e selezionare **Aggiungi > Nuovo elemento...**:

    ![](quickstart-images/vs/add-new-item.png "Aggiungere un nuovo elemento")

10. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Visual C# > Codice > Classe**, assegnare al nuovo file il nome **PhoneTranslator** e fare clic sul pulsante **Aggiungi**:

    ![](quickstart-images/vs/add-translator-class.w157.png "Aggiungere una nuova classe")

11. In **PhoneTranslator.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice convertirà una parola telefonica in un numero telefonico:

    ```csharp
    using System.Text;

    namespace Phoneword
    {
        public static class PhonewordTranslator
        {
            public static string ToNumber(string raw)
            {
                if (string.IsNullOrWhiteSpace(raw))
                    return null;

                raw = raw.ToUpperInvariant();

                var newNumber = new StringBuilder();
                foreach (var c in raw)
                {
                    if (" -0123456789".Contains(c))
                        newNumber.Append(c);
                    else
                    {
                        var result = TranslateToNumber(c);
                        if (result != null)
                            newNumber.Append(result);
                        // Bad character?
                        else
                            return null;
                    }
                }
                return newNumber.ToString();
            }

            static bool Contains(this string keyString, char c)
            {
                return keyString.IndexOf(c) >= 0;
            }

            static readonly string[] digits = {
                "ABC", "DEF", "GHI", "JKL", "MNO", "PQRS", "TUV", "WXYZ"
            };

            static int? TranslateToNumber(char c)
            {
                for (int i = 0; i < digits.Length; i++)
                {
                    if (digits[i].Contains(c))
                        return 2 + i;
                }
                return null;
            }
        }
    }
    ```

    Salvare le modifiche apportate a **PhoneTranslator.cs** premendo **CTRL+S** e chiudere il file.

12. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Phoneword** e selezionare **Aggiungi > Nuovo elemento...**:

    ![](quickstart-images/vs/add-new-item.png "Aggiungere un nuovo elemento")

13. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Visual C# > Codice > Interfaccia**, assegnare al nuovo file il nome **IDialer** e fare clic sul pulsante **Aggiungi**:

    ![](quickstart-images/vs/add-idialer-interface.w157.png "Aggiungere una nuova interfaccia")

14. In **IDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice definisce un metodo `Dial` che deve essere implementato per ogni piattaforma per comporre un numero di telefono convertito:

    ```csharp
    namespace Phoneword
    {
        public interface IDialer
        {
            bool Dial(string number);
        }
    }
    ```

    Salvare le modifiche apportate a **IDialer.cs** premendo **CTRL+S** e chiudere il file.

    > [!NOTE]
    > Il codice comune per l'applicazione è ora completo. Il codice di composizione telefonica specifico della piattaforma verrà ora implementato come oggetto [DependencyService](~/xamarin-forms/app-fundamentals/dependency-service/index.md).

15. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Phoneword.iOS** e selezionare **Aggiungi > Nuovo elemento...**:

    ![](quickstart-images/vs/add-new-item-ios.png "Aggiungere un nuovo elemento")

16. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Apple > Codice > Classe**, assegnare al nuovo file il nome **PhoneDialer** e fare clic sul pulsante **Aggiungi**:

    ![](quickstart-images/vs/new-phone-dialer-ios.w157.png "Aggiungere una nuova classe")

17. In **PhoneDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice crea il metodo <code>Dial</code> che verrà usato nella piattaforma iOS per comporre un numero di telefono convertito:

    ```csharp
    using Foundation;
    using Phoneword.iOS;
    using UIKit;
    using Xamarin.Forms;

    [assembly: Dependency(typeof(PhoneDialer))]
    namespace Phoneword.iOS
    {
        public class PhoneDialer : IDialer
        {
            public bool Dial(string number)
            {
                return UIApplication.SharedApplication.OpenUrl (
                    new NSUrl ("tel:" + number));
            }
        }
    }
    ```

    Salvare le modifiche apportate a **PhoneDialer.cs** premendo **CTRL+S** e chiudere il file.

18. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Phoneword.Android** e selezionare **Aggiungi > Nuovo elemento...**:

    ![](quickstart-images/vs/add-new-item-android.png "Aggiungi nuovo elemento")

19. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Visual C# > Android > Classe**, assegnare al nuovo file il nome **PhoneDialer** e fare clic sul pulsante **Aggiungi**:

    ![](quickstart-images/vs/new-phone-dialer-android.w157.png "Aggiungere una nuova classe")

20. In **PhoneDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice crea il metodo `Dial` che verrà usato nella piattaforma Android per comporre un numero di telefono convertito:

    ```csharp
    using Android.Content;
    using Android.Telephony;
    using Phoneword.Droid;
    using System.Linq;
    using Xamarin.Forms;
    using Uri = Android.Net.Uri;

    [assembly: Dependency(typeof(PhoneDialer))]
    namespace Phoneword.Droid
    {
        public class PhoneDialer : IDialer
        {
            public bool Dial(string number)
            {
                var context = MainActivity.Instance;
                if (context == null)
                    return false;

                var intent = new Intent (Intent.ActionDial);
                intent.SetData (Uri.Parse ("tel:" + number));

                if (IsIntentAvailable (context, intent)) {
                    context.StartActivity (intent);
                    return true;
                }

                return false;
            }

            public static bool IsIntentAvailable(Context context, Intent intent)
            {
                var packageManager = context.PackageManager;

                var list = packageManager.QueryIntentServices (intent, 0)
                    .Union (packageManager.QueryIntentActivities (intent, 0));

                if (list.Any ())
                    return true;

                var manager = TelephonyManager.FromContext (context);
                return manager.PhoneType != PhoneType.None;
            }
        }
    }
    ```

    Si noti che questo codice presuppone l'uso dell'API Android più recente. Salvare le modifiche apportate a **PhoneDialer.cs** premendo **CTRL+S** e chiudere il file.

21. In **Esplora soluzioni**, nel progetto **Phoneword.Android**, fare doppio clic su **MainActivity.cs** per aprirlo, rimuovere tutto il codice del modello e sostituirlo con il codice seguente:

    ```csharp
    using Android.App;
    using Android.Content.PM;
    using Android.OS;

    namespace Phoneword.Droid
    {
        [Activity(Label = "Phoneword", Icon = "@mipmap/icon", Theme = "@style/MainTheme", MainLauncher = true,
                  ConfigurationChanges = ConfigChanges.ScreenSize | ConfigChanges.Orientation)]
        public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
        {
            internal static MainActivity Instance { get; private set; }

            protected override void OnCreate(Bundle bundle)
            {
                TabLayoutResource = Resource.Layout.Tabbar;
                ToolbarResource = Resource.Layout.Toolbar;

                base.OnCreate(bundle);
                Instance = this;
                global::Xamarin.Forms.Forms.Init(this, bundle);
                LoadApplication(new App());
            }
        }
    }
    ```

    Salvare le modifiche apportate a **MainActivity.cs** premendo **CTRL+S** e chiudere il file.

22. Nel progetto **Phoneword.Android** in **Esplora soluzioni** fare doppio clic su **Proprietà** e selezionare la scheda **Manifesto Android**:

    ![](quickstart-images/vs/android-manifest.png "Aprire il file manifesto di Android")

23. Nella sezione **Autorizzazioni necessarie** abilitare l'autorizzazione **CALL_PHONE**. In questo modo l'applicazione è autorizzata a effettuare una chiamata telefonica:

    ![](quickstart-images/vs/android-manifest-changed.png "Abilitare l'autorizzazione CallPhone")

    Salvare le modifiche apportate al manifesto premendo **CTRL+S** e chiudere il file.

24. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Phoneword.UWP** e selezionare **Aggiungi > Nuovo elemento...**:

    ![](quickstart-images/vs/add-new-item-uwp.png "Aggiungere un nuovo elemento")

25. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Visual C# > Codice > Classe**, assegnare al nuovo file il nome **PhoneDialer** e fare clic sul pulsante **Aggiungi**:

    ![](quickstart-images/vs/new-phone-dialer-uwp.w157.png "Aggiungere una nuova classe")

26. In **PhoneDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice crea il metodo `Dial` e i metodi dell'helper che verranno usati nella piattaforma UWP per comporre un numero di telefono convertito:

    ```csharp
    using Phoneword.UWP;
    using System;
    using System.Threading.Tasks;
    using Windows.ApplicationModel.Calls;
    using Windows.UI.Popups;
    using Xamarin.Forms;

    [assembly: Dependency(typeof(PhoneDialer))]
    namespace Phoneword.UWP
    {
        public class PhoneDialer : IDialer
        {
            bool dialled = false;

            public bool Dial(string number)
            {
                DialNumber(number);
                return dialled;
            }

            async Task DialNumber(string number)
            {
                var phoneLine = await GetDefaultPhoneLineAsync();
                if (phoneLine != null)
                {
                    phoneLine.Dial(number, number);
                    dialled = true;
                }
                else
                {
                    var dialog = new MessageDialog("No line found to place the call");
                    await dialog.ShowAsync();
                    dialled = false;
                }
            }

            async Task<PhoneLine> GetDefaultPhoneLineAsync()
            {
                var phoneCallStore = await PhoneCallManager.RequestStoreAsync();
                var lineId = await phoneCallStore.GetDefaultLineAsync();
                return await PhoneLine.FromIdAsync(lineId);
            }
        }
    }
    ```

    Salvare le modifiche apportate a **PhoneDialer.cs** premendo **CTRL+S** e chiudere il file.

27. Nel progetto **Phoneword.UWP** in **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Riferimenti** e selezionare **Aggiungi riferimento...**:

    ![](quickstart-images/vs/uwp-add-reference.png "Aggiungere un riferimento")

28. Nella finestra di dialogo **Gestione riferimenti** selezionare **Windows universale > Estensioni > Windows Mobile Extensions for the UWP** e fare clic sul pulsante **OK**:

    ![](quickstart-images/vs/uwp-add-reference-extensions.png "Aggiungere estensioni di Windows Mobile per UWP")

29. Fare doppio clic su **Package.appxmanifest** nel progetto **Phoneword.UWP** nel **riquadro della soluzione**:

    ![](quickstart-images/vs/uwp-manifest.png "Aprire il manifesto della piattaforma UWP")

30. Nella pagina **Funzionalità** abilitare **Chiamata telefonica**. In questo modo l'applicazione è autorizzata a effettuare una chiamata telefonica:

    ![](quickstart-images/vs/uwp-manifest-changed.png "Abilitare la funzionalità Chiamata telefonica")

    Salvare le modifiche apportate al manifesto premendo **CTRL+S** e chiudere il file.

31. In Visual Studio selezionare la voce di menu **Compila > Compila soluzione** o premere **CTRL+MAIUSC+B**. L'applicazione verrà compilata e nella barra di stato di Visual Studio viene visualizzato un messaggio di operazione completata:

    ![](quickstart-images/vs/build-successful.png "Compilazione completata")

    In caso di errori, ripetere i passaggi precedenti e correggere gli errori fino a quando l'applicazione non viene compilata correttamente.

32. Nel **riquadro della soluzione** fare clic con il pulsante destro del mouse sul progetto **Phoneword.UWP** e selezionare **Imposta come progetto di avvio**:

    ![](quickstart-images/vs/uwp-set-as-startup-project.png "Impostare come progetto di avvio")

33. Nella barra degli strumenti di Visual Studio premere il pulsante **Avvia**, ovvero il pulsante a forma di triangolo simile a un pulsante Riproduci, per avviare l'applicazione:

    ![](quickstart-images/vs/start.png "Barra degli strumenti di Visual Studio")
    ![](quickstart-images/vs/phone-result-uwp.png "UWP applicazione Phoneword")

34. Nel **riquadro della soluzione** fare clic con il pulsante destro del mouse sul progetto **Phoneword.Android** e selezionare **Imposta come progetto di avvio**.
35. Nella barra degli strumenti di Visual Studio premere il pulsante **Avvia**, ovvero il pulsante a forma di triangolo simile a un pulsante Riproduci, per avviare l'applicazione all'interno di un emulatore Android.
36. Se si ha un dispositivo iOS e si soddisfano i requisiti di sistema Mac per lo sviluppo in Xamarin.Forms, usare una tecnica simile per distribuire l'app al dispositivo iOS. In alternativa, distribuire l'app nel [simulatore remoto per iOS](~/tools/ios-simulator.md).

    Nota: non tutti i simulatori supportano le chiamate telefoniche.

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio per Mac](#tab/vsmac)

1. Avviare Visual Studio per Mac e nella pagina iniziale fare clic su **Nuovo progetto...**  per creare un nuovo progetto:

    ![](quickstart-images/xs/new-solution.png "Nuova soluzione")

2. Nella finestra di dialogo **Scegli un modello per il nuovo progetto** fare clic su **Multipiattaforma > App**, selezionare il modello **App Forms vuota** e fare clic sul pulsante **Avanti**:

    ![](quickstart-images/xs/choose-template.png "Scelta di un modello")

3. Nella finestra di dialogo **Configure your Blank Forms app** (Configura le app con i moduli vuoti), denominare la nuova app **Phoneword**, assicurarsi che sia selezionato il pulsante di opzione **Use .NET Standard** (Usa .NET Standard) e selezionare il pulsante **Avanti**:

    ![](quickstart-images/xs/configure-app.png "Configurare l'applicazione Forms")

4. Nella finestra di dialogo **Configure your new Blank Forms app** (Configura la nuova app Forms vuota) lasciare i nomi di soluzione e progetto impostati su **Phoneword**, scegliere un percorso appropriato per il progetto e scegliere il pulsante **Crea** per creare il progetto:

    ![](quickstart-images/xs/configure-project.png "Configurare il progetto Forms")

    > [!NOTE]
    > La mancata denominazione della soluzione e del progetto **Phoneword** comporterà numerosi errori di compilazione.

5. Nel **riquadro della soluzione** fare doppio clic su **MainPage.xaml** per aprirlo:

    ![](quickstart-images/xs/open-mainpage-xaml.png "Aprire MainPage.xaml")

6. In **MainPage.xaml** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice definisce in modo dichiarativo l'interfaccia utente per la pagina:

    ```xaml
    <?xml version="1.0" encoding="UTF-8"?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
                       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
                       x:Class="Phoneword.MainPage">
        <ContentPage.Padding>
            <OnPlatform x:TypeArguments="Thickness">
                <On Platform="iOS" Value="20, 40, 20, 20" />
                <On Platform="Android, UWP" Value="20" />
            </OnPlatform>
        </ContentPage.Padding>
        <StackLayout>
          <Label Text="Enter a Phoneword:" />
          <Entry x:Name="phoneNumberText" Text="1-855-XAMARIN" />
          <Button x:Name="translateButon" Text="Translate" Clicked="OnTranslate" />
          <Button x:Name="callButton" Text="Call" IsEnabled="false" Clicked="OnCall" />
        </StackLayout>
    </ContentPage>
    ```

    Salvare le modifiche apportate a **MainPage.xaml** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

7. Nel **riquadro della soluzione** fare doppio clic su **MainPage.xaml.cs** per aprirlo:

    ![](quickstart-images/xs/open-mainpage-codebehind.png "Aprire MainPage.xaml.cs")

8. In **MainPage.xaml.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. I metodi `OnTranslate` e `OnCall` verranno eseguiti in risposta alla selezione dei pulsanti di **traduzione** e **chiamata** nell'interfaccia utente, rispettivamente:

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace Phoneword
    {
        public partial class MainPage : ContentPage
        {
            string translatedNumber;

            public MainPage ()
            {
                InitializeComponent ();
            }

            void OnTranslate (object sender, EventArgs e)
            {
                translatedNumber = PhonewordTranslator.ToNumber (phoneNumberText.Text);
                if (!string.IsNullOrWhiteSpace (translatedNumber)) {
                    callButton.IsEnabled = true;
                    callButton.Text = "Call " + translatedNumber;
                } else {
                    callButton.IsEnabled = false;
                    callButton.Text = "Call";
                }
            }

            async void OnCall (object sender, EventArgs e)
            {
                if (await this.DisplayAlert (
                        "Dial a Number",
                        "Would you like to call " + translatedNumber + "?",
                        "Yes",
                        "No")) {
                    var dialer = DependencyService.Get<IDialer> ();
                    if (dialer != null)
                        dialer.Dial (translatedNumber);
                }
            }
        }
    }
    ```

    > [!NOTE]
    > Se si prova a compilare l'applicazione a questo punto, si verificano errori che verranno risolti in un secondo momento.

    Salvare le modifiche apportate a **MainPage.xaml.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

9. Nel **riquadro della soluzione** selezionare il progetto **Phoneword**, fare clic con il pulsante destro del mouse e selezionare **Aggiungi > Nuovo file...**:

    ![](quickstart-images/xs/add-new-translator-file.png "Aggiungere un nuovo file")

10. Nella finestra di dialogo **Nuovo file** selezionare **Generale > Classe vuota**, assegnare al nuovo file il nome **PhoneTranslator** e fare clic sul pulsante **Nuovo**:

    ![](quickstart-images/xs/add-translator-class.png "Aggiungere una nuova classe")

11. In **PhoneTranslator.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice convertirà una parola telefonica in un numero telefonico:

    ```csharp
    using System.Text;

    namespace Phoneword
    {
        public static class PhonewordTranslator
        {
            public static string ToNumber(string raw)
            {
                if (string.IsNullOrWhiteSpace(raw))
                    return null;

                raw = raw.ToUpperInvariant();

                var newNumber = new StringBuilder();
                foreach (var c in raw)
                {
                    if (" -0123456789".Contains(c))
                        newNumber.Append(c);
                    else
                    {
                        var result = TranslateToNumber(c);
                        if (result != null)
                            newNumber.Append(result);
                        // Bad character?
                        else
                            return null;
                    }
                }
                return newNumber.ToString();
            }

            static bool Contains(this string keyString, char c)
            {
                return keyString.IndexOf(c) >= 0;
            }

            static readonly string[] digits = {
                "ABC", "DEF", "GHI", "JKL", "MNO", "PQRS", "TUV", "WXYZ"
            };

            static int? TranslateToNumber(char c)
            {
                for (int i = 0; i < digits.Length; i++)
                {
                    if (digits[i].Contains(c))
                        return 2 + i;
                }
                return null;
            }
        }
    }
    ```

    Salvare le modifiche apportate a **PhoneTranslator.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

12. Nel **riquadro della soluzione** selezionare il progetto **Phoneword**, fare clic con il pulsante destro del mouse e selezionare **Aggiungi > Nuovo file...**:

    ![](quickstart-images/xs/add-new-interface.png "Aggiungere un nuovo file")

13. Nella finestra di dialogo **Nuovo file** selezionare **Generale > Interfaccia vuota**, assegnare al nuovo file il nome **IDialer** e fare clic sul pulsante **Nuovo**:

    ![](quickstart-images/xs/add-idialer-interface.png "Aggiungere una nuova interfaccia")

14. In **IDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice definisce un metodo `Dial` che deve essere implementato per ogni piattaforma per comporre un numero di telefono convertito:

    ```csharp
    namespace Phoneword
    {
        public interface IDialer
        {
            bool Dial(string number);
        }
    }
    ```
    Salvare le modifiche apportate a **IDialer.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

    > [!NOTE]
    > Il codice comune per l'applicazione è ora completo. Il codice di composizione telefonica specifico della piattaforma verrà ora implementato come oggetto [DependencyService](~/xamarin-forms/app-fundamentals/dependency-service/index.md).

15. Nel **riquadro della soluzione** selezionare il progetto **Phoneword.iOS**, fare clic con il pulsante destro del mouse e selezionare **Aggiungi > Nuovo file...**:

    ![](quickstart-images/xs/add-new-file-ios.png "Aggiungere un nuovo file")

16. Nella finestra di dialogo **Nuovo file** selezionare **Generale > Classe vuota**, assegnare al nuovo file il nome **PhoneDialer** e fare clic sul pulsante **Nuovo**:

    ![](quickstart-images/xs/new-phonedialer-ios.png "Aggiungere una nuova classe")

17. In **PhoneDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice crea il metodo `Dial` che verrà usato nella piattaforma iOS per comporre un numero di telefono convertito:

    ```csharp
    using Foundation;
    using Phoneword.iOS;
    using UIKit;
    using Xamarin.Forms;

    [assembly: Dependency(typeof(PhoneDialer))]
    namespace Phoneword.iOS
    {
        public class PhoneDialer : IDialer
        {
            public bool Dial(string number)
            {
                return UIApplication.SharedApplication.OpenUrl (
                    new NSUrl ("tel:" + number));
            }
        }
    }
    ```

    Salvare le modifiche apportate a **PhoneDialer.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

18. Nel **riquadro della soluzione** selezionare il progetto **Phoneword.Droid**, fare clic con il pulsante destro del mouse e selezionare **Aggiungi > Nuovo file...**:

    ![](quickstart-images/xs/add-new-file-android.png "Aggiungere un nuovo file")

19. Nella finestra di dialogo **Nuovo file** selezionare **Generale > Classe vuota**, assegnare al nuovo file il nome **PhoneDialer** e fare clic sul pulsante **Nuovo**:

    ![](quickstart-images/xs/new-phonedialer-android.png "Aggiungere una nuova classe")

20. In **PhoneDialer.cs** rimuovere tutto il codice del modello e sostituirlo con il codice seguente. Questo codice crea il metodo `Dial` che verrà usato nella piattaforma Android per comporre un numero di telefono convertito:

    ```csharp
    using Android.Content;
    using Android.Telephony;
    using Phoneword.Droid;
    using System.Linq;
    using Xamarin.Forms;
    using Uri = Android.Net.Uri;

    [assembly: Dependency(typeof(PhoneDialer))]
    namespace Phoneword.Droid
    {
        public class PhoneDialer : IDialer
        {
            public bool Dial(string number)
            {
                var context = MainActivity.Instance;
                if (context == null)
                    return false;

                var intent = new Intent (Intent.ActionDial);
                intent.SetData (Uri.Parse ("tel:" + number));

                if (IsIntentAvailable (context, intent)) {
                    context.StartActivity (intent);
                    return true;
                }

                return false;
            }

            public static bool IsIntentAvailable(Context context, Intent intent)
            {
                var packageManager = context.PackageManager;

                var list = packageManager.QueryIntentServices (intent, 0)
                    .Union (packageManager.QueryIntentActivities (intent, 0));

                if (list.Any ())
                    return true;

                var manager = TelephonyManager.FromContext (context);
                return manager.PhoneType != PhoneType.None;
            }
        }
    }
    ```

    Si noti che questo codice presuppone l'uso dell'API Android più recente. Salvare le modifiche apportate a **PhoneDialer.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

21. Nel **riquadro della soluzione**, nel progetto **Phoneword.Droid**, fare doppio clic su **MainActivity.cs** per aprirlo, rimuovere tutto il codice del modello e sostituirlo con il codice seguente:

    ```csharp
    using Android.App;
    using Android.Content.PM;
    using Android.OS;

    namespace Phoneword.Droid
    {
        [Activity(Label = "Phoneword", Icon = "@mipmap/icon", Theme = "@style/MainTheme", MainLauncher = true,
                  ConfigurationChanges = ConfigChanges.ScreenSize | ConfigChanges.Orientation)]
        public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
        {
            internal static MainActivity Instance { get; private set; }

            protected override void OnCreate(Bundle bundle)
            {
                TabLayoutResource = Resource.Layout.Tabbar;
                ToolbarResource = Resource.Layout.Toolbar;

                base.OnCreate(bundle);
                Instance = this;
                global::Xamarin.Forms.Forms.Init(this, bundle);
                LoadApplication(new App());
            }
        }
    }
    ```

    Salvare le modifiche apportate a **MainActivity.cs** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

22. Nel **riquadro della soluzione** espandere la cartella delle **proprietà** e fare doppio clic sul file **AndroidManifest.xml**:

    ![](quickstart-images/xs/android-manifest.png "Aprire il file manifesto di Android")

23. Nella sezione **Autorizzazioni necessarie** abilitare l'autorizzazione **CallPhone**. In questo modo l'applicazione è autorizzata a effettuare una chiamata telefonica:

    ![](quickstart-images/xs/android-manifest-changed.png "Abilitare l'autorizzazione CallPhone")

    Salvare le modifiche apportate a **AndroidManifest.xml** scegliendo **File > Salva** o premendo **&#8984; + S** e chiudere il file.

24. In Visual Studio per Mac selezionare la voce di menu **Compila > Compila tutto** o premere **&#8984; + B**. L'applicazione viene compilata e verrà visualizzato un messaggio di operazione completata nella barra degli strumenti di Visual Studio per Mac.

    ![](quickstart-images/xs/build-successful.png "Compilazione completata")

25. In caso di errori, ripetere i passaggi precedenti e correggere gli errori fino a quando l'applicazione non viene compilata correttamente.
26. Nella barra degli strumenti di Visual Studio per Mac premere il pulsante **Avvia**, ovvero il pulsante a forma di triangolo simile a un pulsante Riproduci, per avviare l'applicazione all'interno del simulatore iOS:

    ![](quickstart-images/xs/start.png "Barra degli strumenti di Visual Studio per Mac")
    ![](quickstart-images/xs/phoneword-result-ios.png "Simulatore iOS")

    Nota: il simulatore iOS non supporta le chiamate telefoniche.

27. Nel **riquadro della soluzione** selezionare il progetto **Phoneword.Droid**, fare clic con il pulsante destro del mouse e selezionare **Imposta come progetto di avvio**:

    ![](quickstart-images/xs/set-startup-project.png "Impostare come progetto di avvio")

28. Nella barra degli strumenti di Visual Studio per Mac premere il pulsante **Start**, ovvero il pulsante a forma di triangolo simile a un pulsante Play, per avviare l'applicazione all'interno di un emulatore Android:

    ![](quickstart-images/xs/phoneword-result-android.png "Emulatore Android")

    Nota: gli emulatori Android non supportano le chiamate telefoniche.

-----

L'applicazione Xamarin.Forms è stata completata. Nell'[argomento successivo](~/xamarin-forms/get-started/hello-xamarin-forms/deepdive.md) di questa guida vengono esaminati i passaggi eseguiti in questa procedura dettagliata per comprendere i concetti fondamentali dello sviluppo delle applicazioni con Xamarin.Forms.


## <a name="related-links"></a>Collegamenti correlati

- [Accesso a funzionalità native con DependencyService](~/xamarin-forms/app-fundamentals/dependency-service/index.md)
- [Phoneword (sample)](https://developer.xamarin.com/samples/xamarin-forms/Phoneword/) (Phoneword - Esempio)
