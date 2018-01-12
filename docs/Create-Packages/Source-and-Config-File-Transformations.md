---
title: "Quell- und Konfigurationsdateitransformationen für NuGet-Pakete | Microsoft-Dokumentation"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 4/24/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 20991d69-9e2e-4881-bbf2-96ae634e1872
description: "Einzelheiten zur Fähigkeit von NuGet-Paketen, Quellcode und Konfigurationsdateien (XML) nach ihrer Installation zu transformieren."
keywords: "NuGet-Paketinstallation, NuGet-Pakettransformationen, Ändern von Konfigurationsdateien, Ändern von Quellcode"
ms.reviewer:
- karann-msft
- unniravindranathan
- anangaur
ms.openlocfilehash: 89a55716ccbc9043cfce4c7f38ec8ab9a0e2f768
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="transforming-source-code-and-configuration-files"></a>Transformieren von Quellcode und Konfigurationsdateien

Bei Projekten, die die Datei `packages.config` oder `project.json` verwenden, unterstützt NuGet die Fähigkeit, bei Paketinstallationen und -deinstallationen Transformationen an dem Quellcode und den Konfigurationsdateien vorzunehmen.

> [!Note]
> Quell- und Konfigurationsdateitransformationen finden keine Anwendung, wenn ein Paket über [Paketverweise in Projektdateien](../Consume-Packages/Package-References-in-Project-Files.md) installiert wird. 

Bei einer **Quellcodetransformation** wird während der Installation des Pakets eine unidirektionale Tokenersetzung auf Dateien im Ordner `content` des Pakets angewendet. Dabei beziehen sich die Token auf die [Projekteigenschaften](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_) von Visual Studio. Dies bietet Ihnen die Möglichkeit, eine Datei in den Namespace des Projekts einzufügen oder Code anzupassen, der normalerweise in `global.asax` in einem ASP.NET-Projekt eingefügt werden würde.

Bei einer **Konfigurationsdateitransformation** können Sie Dateien ändern, die bereits in einem Zielprojekt vorhanden sind, wie z.B. `web.config` und `app.config`. In Ihrem Paket müsste beispielsweise ein Element zu Abschnitt `modules` in der Konfigurationsdatei hinzugefügt werden. Diese Transformation erfolgt durch das Einschließen spezieller Dateien in das Paket, in denen die zu den Konfigurationsdateien hinzuzufügenden Abschnitte beschrieben werden. Bei der Deinstallation eines Pakets werden diese Änderungen wieder zurückgesetzt, wodurch diese Transformation zu einer bidirektionalen Transformation wird.

## <a name="specifying-source-code-transformations"></a>Angeben von Quellcodetransformationen

1. Dateien, die Sie aus dem Paket in das Projekt einfügen möchten, müssen in dem Ordner `content` des Pakets enthalten sein. Wenn Sie beispielsweise möchten, dass eine Datei mit dem Namen `ContosoData.cs` in dem Ordner `Models` des Zielprojekts installiert wird, muss diese im Ordner `content\Models` des Pakets enthalten sein.

1. Hängen Sie `.pp` an den Namen der Quellcodedatei an, um NuGet die Anweisung zu geben, die Tokenersetzung während der Installation anzuwenden. Nach der Installation weist die Datei nicht die Erweiterung `.pp` auf.

    Wenn Sie beispielsweise Transformationen in `ContosoData.cs` vornehmen möchten, nennen Sie die Datei in dem Paket `ContosoData.cs.pp`. Nach der Installation wird sie als `ContosoData.cs` angezeigt.

1. Verwenden Sie für die Angabe von Werten, die NuGet durch Projekteigenschaften ersetzen sollte, in der Quellcodedatei Token im Format `$token$` ohne Beachtung der Groß-/Kleinschreibung:

    ```cs
    namespace $rootnamespace$.Models
    {
        public struct CategoryInfo
        {
            public string categoryid;
            public string description;
            public string htmlUrl;
            public string rssUrl;
            public string title;
        }
    }
    ```

    Bei der Installation ersetzt NuGet `$rootnamespace$`, wobei es davon ausgeht, dass `Fabrikam` das Zielprojekt ist, dessen Stammnamespace `Fabrikam` lautet.

Das Token `$rootnamespace$` stellt die am häufigsten verwendete Projekteigenschaft dar. Alle weiteren Token werden in der Dokumentation zu [Projekteigenschaften](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_) auf MSDN aufgeführt. Bedenken Sie jedoch, dass einige Eigenschaften möglicherweise für den Projekttyp spezifisch sind.

## <a name="specifying-config-file-transformations"></a>Angeben von Konfigurationsdateitransformationen

Wie in den nachfolgenden Abschnitten beschrieben, können Konfigurationsdateitransformationen auf zwei Arten erfolgen:

- Schließen Sie die Dateien `app.config.transform` und `web.config.transform` in den Ordner `content` Ihres Pakets ein. Dabei erkennt NuGet an der `.transform`-Erweiterung, dass diese Dateien den XML-Code enthalten, der bei der Installation des Pakets mit vorhandenen Konfigurationsdateien zusammengeführt werden soll. Bei der Deinstallation eines Pakets wird derselbe XML-Code entfernt.
- (NuGet ab Version 2.6) Schließen Sie die Dateien `app.config.install.xdt` und `web.config.install.xdt` in den Ordner `content` Ihres Pakets ein, und verwenden Sie dabei [XDT-Syntax](https://msdn.microsoft.com/library/dd465326.aspx) zur Beschreibung der gewünschten Änderungen. Mit dieser Option können Sie auch eine Datei vom Typ `.uninstall.xdt` einschließen, um Änderungen zurückzusetzen, wenn das Paket aus dem Projekt entfernt wird.

> [!Note]
> Transformationen gelten nicht für `.config`-Dateien, auf die ein Link in Visual Studio verweist.

Der Vorteil bei der Verwendung von XDT besteht darin, dass zwei statische Dateien nicht einfach zusammengeführt werden, sondern eine Syntax für die Bearbeitung der Struktur eines Using-Elements in XML DOM sowie eines zugehörigen Attributs mit voller XPath-Unterstützung bereitgestellt wird. XDT kann anschließend Elemente hinzufügen, aktualisieren oder entfernen, Elemente an einer bestimmten Stelle anordnen oder Elemente ersetzen/entfernen (einschließlich untergeordneter Knoten). Dadurch wird die Erstellung von Transformationen zur Deinstallation erleichtert, bei denen sämtliche Transformationen zurückgesetzt werden, die während der Paketinstallation erfolgt sind.

### <a name="xml-transforms"></a>XML-Transformationen

Die Dateien `app.config.transform` und `web.config.transform` in dem Ordner `content` eines Pakets enthalten nur die Elemente, die in den vorhandenen Dateien `app.config` und `web.config` des Projekts zusammengeführt werden sollen.

Angenommen, das Projekt weist zu Beginn folgende Inhalte in der Datei `web.config` auf:

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
        </modules>
    <system.webServer>
</configuration>
```

Wenn Sie ein `MyNuModule`-Element während der Paketinstallation zum Abschnitt `modules` hinzufügen möchten, erstellen Sie im Ordner `content` des Pakets eine Datei vom Typ `web.config.transform`, die wie folgt aussieht:

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

Nach der Installation des Pakets durch NuGet wird die Datei `web.config` wie folgt angezeigt:

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

Beachten Sie, dass NuGet den Abschnitt `modules` nicht ersetzt hat. Der neue Eintrag wurde lediglich durch das Hinzufügen neuer Elemente und Attribute zusammengeführt. NuGet ändert keine vorhandenen Elemente oder Attribute.

Wenn das Paket deinstalliert wird, überprüft NuGet die `.transform`-Dateien erneut und entfernt die enthaltenen Elemente aus den entsprechenden `.config`-Dateien. Beachten Sie, dass dieser Prozess keine Auswirkungen auf die Zeilen in der Datei `.config` hat, die Sie nach der Paketinstallation ändern.

In einem umfangreicheren Beispiel fügt das Paket [Error Logging Modules and Handlers for ASP.NET (ELMAH)](https://www.nuget.org/packages/elmah/) (Module für die Fehlerprotokollierung und Handlers für ASP.NET) viele Einträge zu `web.config` hinzu, die bei der Deinstallation eines Pakets wieder entfernt werden.

Wenn Sie die zugehörige Datei `web.config.transform` überprüfen möchten, laden Sie das ELMAH-Paket über den oben stehenden Link herunter, ändern Sie die Paketerweiterung von `.nupkg` in `.zip`, und öffnen Sie anschließend `content\web.config.transform` in dieser ZIP-Datei.

Erstellen Sie ein neues ASP.NET-Projekt in Visual Studio (die Vorlage ist unter **Visual C# > Web** im Dialogfeld „Neues Projekt“ zu finden), und wählen Sie eine leere ASP.NET-App aus, um die Auswirkungen der Installation und Deinstallation des Pakets sehen zu können. Öffnen Sie `web.config`, um den zugehörigen ursprünglichen Status anzuzeigen. Klicken Sie anschließend mit der rechten Maustaste auf das Projekt, wählen Sie **NuGet-Pakete verwalten** aus, suchen Sie auf der Website nuget.org nach ELMAH, und installieren Sie die neueste Version. Beachten Sie alle an `web.config` vorgenommenen Änderungen. Wenn sie das Paket jetzt deinstallieren, können Sie sehen, wie `web.config` in den zugehörigen ursprünglichen Status zurückversetzt wird.

### <a name="xdt-transforms"></a>XDT-Transformationen

Mit NuGet ab Version 2.6 können Sie Konfigurationsdateien über die [XDT-Syntax](https://msdn.microsoft.com/library/dd465326.aspx) ändern. Sie können auch veranlassen, dass NuGet Token über [Projekteigenschaften](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_) ersetzt, indem der Eigenschaftenname innerhalb der Trennzeichen `$` (ohne Berücksichtigung der Groß-/Kleinschreibung) eingeschlossen wird.

In der folgenden Datei `app.config.install.xdt` wird beispielsweise ein `appSettings`-Element mit den Werten `FullPath`, `FileName`, und `ActiveConfigurationSettings` des Projekts in `app.config` eingefügt:

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <appSettings xdt:Transform="Insert">
        <add key="FullPath" value="$FullPath$" />
        <add key="FileName" value="$filename$" />
        <add key="ActiveConfigurationSettings " value="$ActiveConfigurationSettings$" />
    </appSettings>
</configuration>
```

In einem weiteren Beispiel wird davon ausgegangen, dass das Projekt zu Beginn folgende Inhalte in der Datei `web.config` aufweist:

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
        </modules>
    <system.webServer>
</configuration>
```

Wenn Sie während der Paketinstallation ein `MyNuModule`-Element zum Abschnitt `modules` hinzufügen möchten, würde die Datei `web.config.install.xdt` des Pakets Folgendes enthalten:

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <system.webServer>
        <modules>
            <add name="MyNuModule" type="Sample.MyNuModule" xdt:Transform="Insert" />
        </modules>
    </system.webServer>
</configuration>
```

Nach der Installation des Pakets sieht `web.config` wie folgt aus:

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

Damit während der Deinstallation des Pakets nur das Element `MyNuModule` entfernt wird, sollte die Datei `web.config.uninstall.xdt` Folgendes enthalten:

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <system.webServer>
        <modules>
            <add name="MyNuModule" xdt:Transform="Remove" xdt:Locator="Match(name)" />
        </modules>
    </system.webServer>
</configuration>
```