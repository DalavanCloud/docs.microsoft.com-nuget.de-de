---
title: Erstellen von nativen NuGet-Paketen
description: Informationen über das Erstellen von nativen NuGet-Paketen, die C++-Code statt verwaltetem Code enthalten und in C++-Projekten verwendet werden können.
author: karann-msft
ms.author: karann
ms.date: 01/09/2017
ms.topic: conceptual
ms.openlocfilehash: f054a1cae7328d3e910d11ac1bfc5f98505e5879
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43546532"
---
# <a name="creating-native-packages"></a>Erstellen von nativen Paketen

Ein natives Paket enthält nativen C++-Code anstelle von verwaltetem Code, sodass es innerhalb von C++-Projekten verwendet werden kann. (Lesen Sie hierzu den Absatz zum Thema [Native C++-Pakete](../consume-packages/finding-and-choosing-packages.md#native-c-packages) im Abschnitt zum Thema „Verwenden“.)

Ein Paket muss das Framework `native` als Ziel haben, damit Sie dieses in einem C++-Projekt verwenden können. Derzeit sind diesem Framework keine Versionsnummern zugeordnet, da NuGet alle C++-Projekte gleich behandelt.

> [!Note]
> Schließen Sie im Abschnitt `<tags>` Ihrer `.nuspec`-Datei unbedingt *native* ein, damit andere Entwickler das Paket finden können, indem sie nach diesem Tag suchen.

Native NuGet-Pakete mit dem Ziel `native` stellen dann in den Ordnern `\build`, `\content` und `\tools` Dateien bereit; `\lib` wird in diesem Fall nicht verwendet, da NuGet keine direkten Verweise auf C++-Projekte hinzufügen kann. Ein Paket kann im Ordner `\build` auch Zieldateien und Eigenschaftendateien enthalten, die NuGet automatisch in die Projekte importiert, die das Paket verwenden. Diese Dateien müssen den gleichen Namen wie die Paket-IDs mit den Erweiterungen `.targets` und/oder `.props` aufweisen. Beispielsweise enthält das Paket [cpprestsdk](https://nuget.org/packages/cpprestsdk/) im Ordner `\build` eine Datei des Typs `cpprestsdk.targets`.

Der Ordner `\build` kann für alle NuGet-Pakete und nicht nur für native Pakete verwendet werden. Der Ordner `\build` berücksichtigt Zielframeworks ebenso wie die Ordner `\content`, `\lib` und `\tools`. Dies bedeutet, dass Sie einen Ordner namens `\build\net40` und einen namens `\build\net45` erstellen können und NuGet die entsprechenden Eigenschaftendateien und Zieldateien dann in das Projekt importiert. (PowerShell-Skripts sind zum Importieren von MSBuild-Zielen nicht erforderlich.)
