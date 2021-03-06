---
title: Veröffentlichen von NuGet-Symbolpaketen mithilfe des neuen Formats für Symbolpakete „.snupkg“ | Microsoft-Dokumentation
author:
- cristinamanu
- kraigb
ms.author:
- cristinamanu
- kraigb
manager: skofman
ms.date: 10/30/2018
ms.topic: reference
ms.prod: nuget
ms.technology: ''
description: Erstellen von NuGet-Symbolpaketen (.snupkg)
keywords: NuGet-Symbolpakete, Debugging von NuGet-Paketen, Unterstützung von NuGet-Debugging, Paketsymbole, Symbolpaketkonventionen
ms.reviewer:
- anangaur
- karann
ms.openlocfilehash: 48ca4b62e722988b3dfe69306565d7f159805962
ms.sourcegitcommit: 0c5a49ec6e0254a4e7a9d8bca7daeefb853c433a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52453454"
---
# <a name="creating-symbol-packages-snupkg"></a>Erstellen von Symbolpaketen (.snupkg)

## <a name="prerequisites"></a>Erforderliche Komponenten

[nuget.exe v4.9.0 oder höher](https://www.nuget.org/downloads) oder [dotnet.exe v2.2.0 oder höher](https://www.microsoft.com/net/download/dotnet-core/2.2), die die erforderlichen [NuGet-Protokolle](../api/nuget-protocols.md) implementieren.

## <a name="creating-a-symbol-package"></a>Erstellen eines Symbolpakets

Ein SNUPKG-Symbolpaket kann über eine NUSPEC-Datei oder eine CSPROJ-Datei erstellt werden. NuGet.exe und dotnet.exe werden jeweils unterstützt. Wenn die Optionen ```-Symbols -SymbolPackageFormat snupkg``` für den nuget.exe-Befehl „pack“ verwendet werden, wird eine SNUPKG-Datei zusätzlich zur NUPKG-Datei erstellt.

Beispielbefehle zum Erstellen von SNUPKG-Dateien
```
dotnet pack MyPackage.csproj --include-symbols -p:SymbolPackageFormat=snupkg

nuget pack MyPackage.nuspec -Symbols -SymbolPackageFormat snupkg

nuget pack MyPackage.csproj -Symbols -SymbolPackageFormat snupkg

msbuild -t:pack MyPackage.csproj -p:IncludeSymbols=true -p:SymbolPackageFormat=snupkg
```

`.snupkgs` werden nicht standardmäßig erstellt. Im Fall von nuget.exe müssen die `SymbolPackageFormat`-Eigenschaft zusammen mit `-Symbols` übergeben, im Fall von dotnet.exe `--include-symbols` und für MSBuild `-p:IncludeSymbols`.

Die Eigenschaft SymbolsPackageFormat kann einen von zwei Werten besitzen: `symbols.nupkg` (Standard) oder `snupkg`. Wenn die SymbolsPackageFormat-Eigenschaft nicht angegeben ist, wird standardmäßig `symbols.nupkg` festgelegt, und ein älteres Symbolpaket wird erstellt.

> [!Note]
> Das ältere Format `.symbols.nupkg` wir noch immer unterstützt, jedoch nur aus Kompatibilitätsgründen (weitere Informationen unter [Erstellen von Symbolpaketen](Symbol-Packages.md)). Der NuGet.org-Symbolserver akzeptiert nur das neue Symbolpaketformat `.snupkg`.

## <a name="publishing-a-symbol-package"></a>Veröffentlichen eines Symbolpakets

1. Speichern Sie zunächst der Einfachheit halber Ihren API-Schlüssel mit NuGet (weitere Informationen unter [publish a package (Veröffentlichen eines Pakets)](../create-packages/publish-a-package.md)).

    ```cli
    nuget SetApiKey Your-API-Key
    ```

1. Nachdem Sie Ihr primäres Paket auf nuget.org veröffentlicht haben, übertragen Sie Ihr Symbol mithilfe von Push wie hier dargestellt:

    ```cli
    nuget push MyPackage.snupkg
    ```

1. Sie können mit dem folgenden Befehl auch das primäre Paket und Symbolpakete gleichzeitig mithilfe von Push übertragen, um Zeit zu sparen. Die NUPKG- und SNUPKG-Dateien müssen jeweils im aktuellen Ordner vorhanden sein.

    ```cli
    nuget push MyPackage.nupkg
    ```

NuGet veröffentlicht beide Pakete auf nuget.org. `MyPackage.nupkg` wird zuerst veröffentlicht, gefolgt von `MyPackage.snupkg`.

## <a name="nugetorg-symbol-server"></a>NuGet.org-Symbolserver

NuGet.org unterstützt das eigene Symbolserverrepository und akzeptiert ausschließlich das neue Symbolpaketformat `.snupkg`. Paketverbraucher können die auf nuget.org-Symbolservern veröffentlichen Symbole verwenden, indem sie `https://symbols.nuget.org/download/symbols` zu ihren Symbolquellen in Visual Studio hinzufügen, wodurch Paketcode im Visual Studio Debugger schrittweise verwendet werden kann. Weitere Einzelheiten zu diesem Prozess finden Sie unter [Angeben von Symbol- (PDB) und Quelldateien im Visual Studio Debugger](https://docs.microsoft.com/en-us/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger?view=vs-2017).

### <a name="nugetorg-symbol-package-constraints"></a>Einschränkungen für nuget.org-Symbolpakete

Die auf nuget.org unterstützten Symbolpakete unterliegen den folgenden Einschränkungen

- Es dürfen ausschließlich die folgenden Dateierweiterungen an ein Symbolpaket angefügt werden. ```.pdb,.nuspec,.xml,.psmdcp,.rels,.p7s```
- Auf dem NuGet-Symbolserver werden derzeit nur verwaltete und [portable PDB-Dateien](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.Metadata/specs/PortablePdb-Metadata.md) unterstützt.
- Die PDB-Dateien und zugehörigen NUPKG-DLLs müssen mit dem Compiler in Visual Studio 15.9 oder höher erstellt worden sein (weiter Informationen unter [pdb crypto hash (Kryptografiehash für PDB-Dateien)](https://github.com/dotnet/roslyn/issues/24429)).

Das auf nuget.org veröffentlichte Symbolpaket schlägt fehl, wenn ein anderer Dateityp in der SNUPKG-Datei enthalten ist.

### <a name="symbol-package-validation-and-indexing"></a>Symbolpaketvalidierung und -indizierung

Per Push an [NuGet.org](https://www.nuget.org/) übertragene Symbolpakete werden verschiedenen Prüfungen, wie z.B. auf Viren, unterzogen.

Wenn das Paket alle Validierungsüberprüfungen bestanden hat, kann es dennoch eine Weile dauern, bis die Symbole indiziert werden und zur Nutzung über die NuGet.org-Symbolserver bereitstehen. Wenn das Paket eine Validierungsüberprüfung nicht besteht, wird die Paketdetailansicht für NUPKG aktualisiert und zeigt den entsprechenden Fehler an. Auch dann erhalten Sie eine E-Mail-Benachrichtigung.

Die Validierung und Indizierung eines Pakets nimmt für gewöhnlich unter 15 Minuten in Anspruch. Wenn das Veröffentlichen des Pakets längere Zeit als erwartet in Anspruch nimmt, besuchen Sie [status.nuget.org](https://status.nuget.org/), um zu überprüfen, ob gerade eine Störung auf nuget.org vorliegt. Wenn alle Systeme in Betrieb sind und das Paket innerhalb einer Stunde nicht erfolgreich veröffentlicht wurde, melden Sie sich auf nuget.org an, und informieren Sie uns über den Link zum Support auf der Paketdetailseite.

## <a name="symbol-package-structure"></a>Symbolpaketstruktur

Die NUPKG-Datei wäre genau dieselbe wie heute, die SNUPKG-Datei würde jedoch folgende Eigenschaften aufweisen:

1) Die SNUPKG-Datei besitzt dieselbe ID und Version wie die entsprechende NUPKG-Datei.
2) Für jede DLL- oder EXE-Datei enthält die SNUPKG-Datei dann dieselbe Ordnerstruktur wie die NUPKG-Datei, mit dem einzigen Unterschied, dass die entsprechenden PDB-Dateien in der gleichen Ordnerhierarchie eingeschlossen werden würden (anstelle der DLL-/EXE-Dateien). Dateien und Ordner mit anderen Erweiterungen als PDB werden aus der SNUPKG-Datei ausgeschlossen.
3) Die NUSPEC-Datei im SNUPKG-Paket gibt auch einen neuen PackageType an, so wie unten dargestellt. Dieser sollte der einzige angegebene PackageType sein. 
``` 
<packageTypes>
  <packageType name="SymbolsPackage"/>
</packageTypes>
```
4) Wenn sich ein Autor dazu entscheidet, eine benutzerdefinierte NUSPEC-Datei für die Erstellung von NUPKG- und SNUPKG-Dateien zu verwenden, muss die SNUPKG-Datei über die gleiche Ordnerhierarchie und die gleichen Dateien wie unter Punkt 2 beschrieben verfügen.
5) Die Felder ```authors``` und ```owners``` werden aus der NUSPEC-Datei von SNUPKG ausgeschlossen.

## <a name="see-also"></a>Siehe auch

[NuGet-Package-Debugging-&-Symbols-Improvements (Verbesserungen für das Debuggen und die Symbole von NuGet-Paketen)](https://github.com/NuGet/Home/wiki/NuGet-Package-Debugging-&-Symbols-Improvements)
