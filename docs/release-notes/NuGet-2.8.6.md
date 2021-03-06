---
title: Anmerkungen zu NuGet 2.8.6
description: Anmerkungen zu dieser Version für die Einbindung von NuGet 2.8.6 bekannte Probleme, Fehlerkorrekturen, hinzugefügter Features und DCRs.
author: karann-msft
ms.author: karann
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: d57c658999ed3c79b962de84fd973276833ef3fd
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2018
ms.locfileid: "43546490"
---
# <a name="nuget-286-release-notes"></a>Anmerkungen zu NuGet 2.8.6

[Anmerkungen zu NuGet 2.8.5](../release-notes/nuget-2.8.5.md) | [Anmerkungen zu NuGet 2.8.7](../release-notes/nuget-2.8.7.md)

NuGet 2.8.6 kam 20. Juli 2015 als geringfügiges Update auf unsere 2.8.5 VSIX mit einigen ausgerichtet, Korrekturen und Verbesserungen für die Unterstützung für Pakete, die Nachrichten übermittelt werden können mit Unterstützung für das Windows 10-UWP-Entwicklungsmodell.

Diese Version von NuGet-Paket-Manager-Erweiterung bietet nur Unterstützung für Visual Studio 2013.

In dieser Version musste das NuGet-Paket-Manager-Dialogfeld Unterstützung für hinzugefügt:

* Die UAP-Ziel-Frameworklinkpfad zur Unterstützung von Windows 10-Anwendungsentwicklung, eingeführt.
* NuGet-Version 3-protokollendpunkte
* Unterstützung für ["NuGet.config"](../consume-packages/configuring-nuget-behavior.md) ProtocolVersion-Attribut für repositoryquellen. Standardwert ist "2"
* Fallback auf remote-Repository, wenn der Zugriff auf die Version ein erforderliches Paket im lokalen Cache nicht verfügbar ist