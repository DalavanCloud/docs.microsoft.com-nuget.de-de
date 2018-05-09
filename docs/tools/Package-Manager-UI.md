---
title: Benutzeroberflächenreferenz für NuGet-Paket-Manager
description: Anweisungen für die Verwendung der NuGet-Paket-Manager-UI in Visual Studio für die Arbeit mit NuGet-Pakete.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 12/08/2017
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
- vs.nuget.packagemanager.ui
ms.openlocfilehash: 99bd51798460a56cb8515d46791a9e75d9e630cc
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="nuget-package-manager-ui"></a><span data-ttu-id="e9b69-103">NuGet-Paket-Manager-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="e9b69-103">NuGet Package Manager UI</span></span>

<span data-ttu-id="e9b69-104">Die NuGet-Paket-Manager-UI in Visual Studio unter Windows können Sie problemlos installieren, deinstallieren und Aktualisieren von NuGet-Pakete in Projekten und Projektmappen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-104">The NuGet Package Manager UI in Visual Studio on Windows allows you to easily install, uninstall, and update NuGet packages in projects and solutions.</span></span> <span data-ttu-id="e9b69-105">Die Erfahrung in Visual Studio für Mac, finden Sie unter [einschließlich eines NuGet-Paket im Projekt](/visualstudio/mac/nuget-walkthrough).</span><span class="sxs-lookup"><span data-stu-id="e9b69-105">For the experience in Visual Studio for Mac, see [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span> <span data-ttu-id="e9b69-106">Die Paket-Manager-UI kann nicht mit Visual Studio-Code enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e9b69-106">The Package Manager UI is not included with Visual Studio Code.</span></span>

<span data-ttu-id="e9b69-107">In diesem Thema:</span><span class="sxs-lookup"><span data-stu-id="e9b69-107">In this topic:</span></span>

- [<span data-ttu-id="e9b69-108">Suchen und installieren ein Paket (Registerkarte "Durchsuchen")</span><span class="sxs-lookup"><span data-stu-id="e9b69-108">Finding and installing a package (Browse tab)</span></span>](#finding-and-installing-a-package)
- [<span data-ttu-id="e9b69-109">Deinstallieren ein Paket (Registerkarte "installiert")</span><span class="sxs-lookup"><span data-stu-id="e9b69-109">Uninstalling a package (Installed tab)</span></span>](#uninstalling-a-package)
- <span data-ttu-id="e9b69-110">[Aktualisieren eines Pakets (Registerkarten installiert und Updates)](#updating-a-package) (enthält die ["Implizit auf die verwiesen wird durch ein SDK" oder "AutoReferenced" Nachricht](#implicit_reference))</span><span class="sxs-lookup"><span data-stu-id="e9b69-110">[Updating a package (Installed and Updates tabs)](#updating-a-package) (includes the ["Implicitly referenced by an SDK" or "AutoReferenced" message](#implicit_reference))</span></span>
- <span data-ttu-id="e9b69-111">[Verwalten von Paketen für die Projektmappe](#managing-packages-for-the-solution) (Arbeiten mit mehreren Projekten gleichzeitig).</span><span class="sxs-lookup"><span data-stu-id="e9b69-111">[Managing packages for the solution](#managing-packages-for-the-solution) (working with multiple projects at the same time).</span></span>
- [<span data-ttu-id="e9b69-112">Paketquellen</span><span class="sxs-lookup"><span data-stu-id="e9b69-112">Package sources</span></span>](#package-sources)
- [<span data-ttu-id="e9b69-113">Paket-Manager-Optionen steuern</span><span class="sxs-lookup"><span data-stu-id="e9b69-113">Package manager Options control</span></span>](#package-manager-options-control)

> [!Note]
> <span data-ttu-id="e9b69-114">Wenn Sie das NuGet-Paket-Manager in Visual Studio 2015 nicht vorhanden sind, überprüfen Sie **Tools > Erweiterungen und Updates...**  , suchen Sie nach der *NuGet Package Manager* Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="e9b69-114">If you're missing the NuGet Package Manager in Visual Studio 2015, check **Tools > Extensions and Updates...** and search for the *NuGet Package Manager* extension.</span></span> <span data-ttu-id="e9b69-115">Wenn Sie nicht das Installationsprogramm für Erweiterungen in Visual Studio verwenden möchten, laden Sie die Erweiterung direkt aus [ https://dist.nuget.org/index.html ](https://dist.nuget.org/index.html).</span><span class="sxs-lookup"><span data-stu-id="e9b69-115">If you're unable to use the extensions installer in Visual Studio, download the extension directly from [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html).</span></span>
>
> <span data-ttu-id="e9b69-116">In Visual Studio 2017 werden NuGet und NuGet-Paket-Manager automatisch mit installiert. NET-bezogenen Arbeitslasten.</span><span class="sxs-lookup"><span data-stu-id="e9b69-116">In Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed with any .NET-related workloads.</span></span> <span data-ttu-id="e9b69-117">Dazu einzeln Installieren der **Einzelkomponenten > Code Extras > NuGet-Paket-Manager** -Option in Visual Studio 2017 Installationsprogramm.</span><span class="sxs-lookup"><span data-stu-id="e9b69-117">Install it individually by selecting the **Individual components > Code tools > NuGet package manager** option in the Visual Studio 2017 installer.</span></span>

## <a name="finding-and-installing-a-package"></a><span data-ttu-id="e9b69-118">Suchen und Installieren eines Pakets</span><span class="sxs-lookup"><span data-stu-id="e9b69-118">Finding and installing a package</span></span>

1. <span data-ttu-id="e9b69-119">In **Projektmappen-Explorer**, mit der rechten Maustaste entweder **Verweise** oder ein Projekt, und wählen **NuGet-Pakete verwalten...** .</span><span class="sxs-lookup"><span data-stu-id="e9b69-119">In **Solution Explorer**, right-click either **References**  or a project and select **Manage NuGet Packages...**.</span></span>

    ![Menüoption für NuGet-Pakete verwalten](media/ManagePackagesUICommand.png)

1. <span data-ttu-id="e9b69-121">Die **Durchsuchen** Registerkarte zeigt die Pakete nach verwendungshäufigkeit von der aktuell ausgewählten Quelle (finden Sie unter [Paket Quellen](#package-sources)).</span><span class="sxs-lookup"><span data-stu-id="e9b69-121">The **Browse** tab displays packages by popularity from the currently selected source (see [package sources](#package-sources)).</span></span> <span data-ttu-id="e9b69-122">Suchen Sie nach einem bestimmten Paket mithilfe des Suchfelds auf der linken oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="e9b69-122">Search for a specific package using the search box on the upper left.</span></span> <span data-ttu-id="e9b69-123">Wählen Sie ein Paket aus der Liste, um dessen Informationen anzuzeigen, wodurch die können auch die **installieren** zusammen mit einem Versionsauswahl Dropdown-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e9b69-123">Select a package from the list to display its information, which also enables the **Install** button along with a version-selection drop-down.</span></span>

    ![Verwalten von NuGet-Pakete Dialogfeld Durchsuchen Registerkarte](media/Search.png)

1. <span data-ttu-id="e9b69-125">Wählen Sie die gewünschte Version aus der Dropdownliste aus, und wählen Sie **installieren**.</span><span class="sxs-lookup"><span data-stu-id="e9b69-125">Select the desired version from the drop-down and select **Install**.</span></span> <span data-ttu-id="e9b69-126">Visual Studio installiert das Paket und seine Abhängigkeiten im Projekt.</span><span class="sxs-lookup"><span data-stu-id="e9b69-126">Visual Studio installs the package and its dependencies into the project.</span></span> <span data-ttu-id="e9b69-127">Möglicherweise werden Sie aufgefordert, Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="e9b69-127">You may be asked to accept license terms.</span></span> <span data-ttu-id="e9b69-128">Nach Abschluss der Installation zusätzliche Pakete angezeigt werden, auf die **installiert** Registerkarte. Pakete werden ebenfalls aufgeführt, der **Verweise** Knoten des Projektmappen-Explorer, der angibt, dass Sie im Projekt die darauf verweisen können `using` Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-128">When installation is complete, the added packages appear on the **Installed** tab. Packages are also listed in the **References** node of Solution Explorer, indicating that you can refer to them in the project with `using` statements.</span></span>

    ![Verweise im Projektmappen-Explorer](media/References.png)

> [!Tip]
> <span data-ttu-id="e9b69-130">Vorabversionen in die Suche einbeziehen und Vorabversionen Dropdown-in der Version verfügbar machen möchten, wählen Sie die **Vorabversion einschließen** Option.</span><span class="sxs-lookup"><span data-stu-id="e9b69-130">To include prerelease versions in the search, and to make prerelease versions available in the version drop-down, select the **Include prerelease** option.</span></span>

## <a name="uninstalling-a-package"></a><span data-ttu-id="e9b69-131">Deinstallieren eines Pakets</span><span class="sxs-lookup"><span data-stu-id="e9b69-131">Uninstalling a package</span></span>

1. <span data-ttu-id="e9b69-132">In **Projektmappen-Explorer**, mit der rechten Maustaste entweder **Verweise** oder das gewünschte Projekt, und die Select **NuGet-Pakete verwalten...** .</span><span class="sxs-lookup"><span data-stu-id="e9b69-132">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**.</span></span>
1. <span data-ttu-id="e9b69-133">Wählen Sie die **installiert** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="e9b69-133">Select the **Installed** tab.</span></span>
1. <span data-ttu-id="e9b69-134">Wählen Sie das Paket deinstallieren (mithilfe der Suche zum Filtern der Liste aus, falls erforderlich), und wählen **Deinstallieren**.</span><span class="sxs-lookup"><span data-stu-id="e9b69-134">Select the package to uninstall (using search to filter the list if necessary) and select **Uninstall**.</span></span>

    ![Deinstallieren eines Pakets](media/UninstallPackage.png)

1. <span data-ttu-id="e9b69-136">Beachten Sie, dass die **Include Vorabversion** und **Paketquelle** Steuerelemente haben keine Auswirkungen, wenn Sie Pakete zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="e9b69-136">Note that the **Include prerelease** and **Package source** controls have no effect when uninstalling packages.</span></span>

## <a name="updating-a-package"></a><span data-ttu-id="e9b69-137">Aktualisieren eines Pakets</span><span class="sxs-lookup"><span data-stu-id="e9b69-137">Updating a package</span></span>

1. <span data-ttu-id="e9b69-138">In **Projektmappen-Explorer**, mit der rechten Maustaste entweder **Verweise** oder das gewünschte Projekt, und die Select **NuGet-Pakete verwalten...** . (Websiteprojekte, mit der Maustaste die **"bin"** Ordner.)</span><span class="sxs-lookup"><span data-stu-id="e9b69-138">In **Solution Explorer**, right-click either **References** or the desired project, and select **Manage NuGet Packages...**. (In web site projects, right-click the **Bin** folder.)</span></span>
1. <span data-ttu-id="e9b69-139">Wählen Sie die **Updates** Registerkarte ", um Pakete anzuzeigen, die aus der ausgewählten Paketquellen verfügbaren Updates verfügen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-139">Select the **Updates** tab to see packages that have available updates from the selected package sources.</span></span> <span data-ttu-id="e9b69-140">Wählen Sie **Vorabversion einschließen** Vorabversionen von Paketen in der Updateliste eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-140">Select **Include prerelease** to include prerelease packages in the update list.</span></span>
1. <span data-ttu-id="e9b69-141">Wählen Sie das Paket zu aktualisieren, wählen die gewünschte Version aus der Dropdownliste auf der rechten Seite, und wählen Sie **aktualisieren**.</span><span class="sxs-lookup"><span data-stu-id="e9b69-141">Select the package to update, select the desired version from the drop-down on the right, and select **Update**.</span></span>

    ![Aktualisieren eines Pakets](media/UpdatePackages.png)

1. <a name="implicit_reference"></a><span data-ttu-id="e9b69-143">Für einige Pakete die **Update** Schaltfläche ist deaktiviert, und eine Meldung angezeigt, die besagt, dass "implizit ein SDK verweist" (oder "AutoReferenced").</span><span class="sxs-lookup"><span data-stu-id="e9b69-143">For some packages, the **Update** button is disabled and a message appears saying that it's "Implicitly referenced by an SDK" (or "AutoReferenced").</span></span> <span data-ttu-id="e9b69-144">Die Meldung gibt an, dass das Paket, z. B. Microsoft.NETCore.App oder Microsoft.NETStandard.Library, Teil eines größeren Framework oder SDK ist und nicht unabhängig voneinander aktualisiert werden sollten.</span><span class="sxs-lookup"><span data-stu-id="e9b69-144">The message indicates that the package, such as Microsoft.NETCore.App or Microsoft.NETStandard.Library, is part of a larger framework or SDK and should not be updated independently.</span></span> <span data-ttu-id="e9b69-145">(Solche Pakete sind intern mit markierten `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) Um das Paket zu aktualisieren, aktualisieren Sie das SDK zu dem er gehört.</span><span class="sxs-lookup"><span data-stu-id="e9b69-145">(Such packages are internally marked with `<IsImplicitlyDefined>True</IsImplicitlyDefined>`.) To update the package, update the SDK to which it belongs.</span></span>

    ![Beispielpaket als implizit gekennzeichnet sein, Verweise oder AutoReferenced](media/PackageManagerUIAutoReferenced.png)

1. <span data-ttu-id="e9b69-147">Um mehrere Pakete auf die neuesten Version zu aktualisieren, wählen sie in der Liste aus und wählen Sie die **aktualisieren** Schaltfläche über der Liste.</span><span class="sxs-lookup"><span data-stu-id="e9b69-147">To update multiple packages to their newest versions, select  them in the list and select the **Update** button above the list.</span></span>
1. <span data-ttu-id="e9b69-148">Sie können auch ein einzelnes Paket aus Aktualisieren der **installiert** Registerkarte. In diesem Fall enthalten die Details für das Paket einen Selektor Version (unterliegen die **Include Vorabversion** Option) und ein **Update** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e9b69-148">You can also update an individual package from the **Installed** tab. In this case, the details for the package include a version selector (subject to the **Include prerelease** option) and an **Update** button.</span></span>

## <a name="managing-packages-for-the-solution"></a><span data-ttu-id="e9b69-149">Verwalten von Paketen für die Projektmappe</span><span class="sxs-lookup"><span data-stu-id="e9b69-149">Managing packages for the solution</span></span>

<span data-ttu-id="e9b69-150">Verwalten von Paketen für eine Projektmappe ist eine bequeme Möglichkeit gleichzeitig mit mehreren Projekten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="e9b69-150">Managing packages for a solution is a convenient means to work with multiple projects simultaneously.</span></span>

1. <span data-ttu-id="e9b69-151">Wählen Sie die **Extras > NuGet-Paket-Manager > NuGet-Pakete für Projektmappe verwalten...**  Menü-Befehls oder mit der rechten Maustaste in der Projektmappe, und wählen Sie **NuGet-Pakete verwalten...** :</span><span class="sxs-lookup"><span data-stu-id="e9b69-151">Select the **Tools > NuGet Package Manager > Manage NuGet Packages for Solution...** menu command, or right-click the solution and select **Manage NuGet Packages...**:</span></span>

    ![Verwalten von NuGet-Pakete für die Projektmappe](media/ManagePackagesSolutionUICommand.png)

1. <span data-ttu-id="e9b69-153">Wenn Sie Pakete für die Projektmappe zu verwalten, kann die Benutzeroberfläche Sie die Projekte auswählen, die von den Vorgängen betroffen sind:</span><span class="sxs-lookup"><span data-stu-id="e9b69-153">When managing packages for the solution, the UI lets you select the projects that are affected by the operations:</span></span>

    ![Projekt-Selektor beim Verwalten von Paketen für die Projektmappe](media/SolutionPackagesUI.png)

### <a name="consolidate-tab"></a><span data-ttu-id="e9b69-155">Registerkarte "Konsolidieren</span><span class="sxs-lookup"><span data-stu-id="e9b69-155">Consolidate tab</span></span>

<span data-ttu-id="e9b69-156">Entwickler halten es in der Regel nicht üblich, verschiedene Versionen desselben NuGet-Pakets über verschiedene Projekte in der gleichen Projektmappe verwenden.</span><span class="sxs-lookup"><span data-stu-id="e9b69-156">Developers typically consider it bad practice to use different versions of the same NuGet package across different projects in the same solution.</span></span> <span data-ttu-id="e9b69-157">Wenn Sie zum Verwalten von Paketen für eine Projektmappe auswählen, die Paket-Manager-UI bietet eine **konsolidieren** Registerkarte auf dem können Sie problemlos nachvollziehen, in denen Pakete mit unterschiedlichen Versionsnummern von verschiedenen Projekten in der Projektmappe verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="e9b69-157">When you choose to manage packages for a solution, the Package Manager UI provides a **Consolidate** tab on which you can easily see where packages with distinct version numbers are used by different projects in the solution:</span></span>

![Paket-Manager-Benutzeroberfläche konsolidieren Registerkarte](media/ConsolidateTab.png)

<span data-ttu-id="e9b69-159">In diesem Beispiel wird das Projekt "ClassLibrary1" EntityFramework 6.2.0 fest, verwendet, wohingegen ConsoleApp1 EntityFramework 6.1.0 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e9b69-159">In this example, the ClassLibrary1 project is using EntityFramework 6.2.0, whereas ConsoleApp1 is using EntityFramework 6.1.0.</span></span> <span data-ttu-id="e9b69-160">Führen Sie folgende Schritte aus, um Paketversionen zu konsolidieren:</span><span class="sxs-lookup"><span data-stu-id="e9b69-160">To consolidate package versions, do the following:</span></span>

- <span data-ttu-id="e9b69-161">Wählen Sie die Projekte in der Projektliste aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e9b69-161">Select the projects to update in the project list.</span></span>
- <span data-ttu-id="e9b69-162">Wählen Sie die Version, verwenden Sie diese Projekte in der **Version** Kontrolle, z. B. EntityFramework 6.2.0 fest.</span><span class="sxs-lookup"><span data-stu-id="e9b69-162">Select the version to use in all those projects in the **Version** control, such as EntityFramework 6.2.0.</span></span>
- <span data-ttu-id="e9b69-163">Wählen Sie die **installieren** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e9b69-163">Select the **Install** button.</span></span>

<span data-ttu-id="e9b69-164">Die Paket-Manager installiert die Version des ausgewählten Pakets in allen ausgewählten Projekte nach dem das Paket nicht mehr angezeigt wird auf die **konsolidieren** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="e9b69-164">The Package Manager installs the selected package version into all selected projects, after which the package no longer appears on the **Consolidate** tab.</span></span>

## <a name="package-sources"></a><span data-ttu-id="e9b69-165">Paketquellen</span><span class="sxs-lookup"><span data-stu-id="e9b69-165">Package sources</span></span>

<span data-ttu-id="e9b69-166">Wählen Sie eine aus dem Quell-Selektor Schritte aus, um die Quelle zu ändern, aus dem Visual Studio ruft Pakete ab:</span><span class="sxs-lookup"><span data-stu-id="e9b69-166">To change the source from which Visual Studio obtains packages, select one from the source selector:</span></span>

![Paket-Quelle-Selektor in der Paket-Manager-Benutzeroberfläche](media/PackageSourceDropDown.png)

<span data-ttu-id="e9b69-168">So verwalten Sie die Paketquellen überein:</span><span class="sxs-lookup"><span data-stu-id="e9b69-168">To manage package sources:</span></span>

1. <span data-ttu-id="e9b69-169">Wählen Sie die **Einstellungen** Symbol in der Paket-Manager-UI unten beschriebenen, oder verwenden Sie die **Tools > Optionen** Befehl und einen Bildlauf zu **NuGet Package Manager**:</span><span class="sxs-lookup"><span data-stu-id="e9b69-169">Select the **Settings** icon in the Package Manager UI outlined below or use the **Tools > Options** command and scroll to **NuGet Package Manager**:</span></span>

    ![Symbol "Einstellungen" Paket-Manager-Benutzeroberfläche](media/PackageSourceSettings.png)

1. <span data-ttu-id="e9b69-171">Wählen Sie die **Paketquellen** Knoten:</span><span class="sxs-lookup"><span data-stu-id="e9b69-171">Select the **Package Sources** node:</span></span>

    ![Quellen Paketoptionen](media/options.png)

1. <span data-ttu-id="e9b69-173">Wählen Sie zum Hinzufügen einer Quelle **+**, bearbeiten Sie den Namen, geben Sie die URL oder Pfad in der **Quelle** Steuerelement, und wählen Sie **Update**.</span><span class="sxs-lookup"><span data-stu-id="e9b69-173">To add a source, select **+**, edit the name, enter the URL or path in the **Source** control, and select  **Update**.</span></span> <span data-ttu-id="e9b69-174">Die Quelle wird jetzt in der Dropdownliste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e9b69-174">The source now appears in the selector drop-down.</span></span>
1. <span data-ttu-id="e9b69-175">Um eine Paketquelle zu ändern, wählen Sie ihn, nehmen Sie Änderungen vor, in der **Namen** und **Quelle** ein, und wählen Sie **Update**.</span><span class="sxs-lookup"><span data-stu-id="e9b69-175">To change a package source, select it, make edits in the **Name** and **Source** boxes, and select **Update**.</span></span>
1. <span data-ttu-id="e9b69-176">Um eine Paketquelle zu deaktivieren, deaktivieren Sie das Kontrollkästchen links neben dem Namen in der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="e9b69-176">To disable a package source, clear the box to the left of the name in the list.</span></span>
1. <span data-ttu-id="e9b69-177">Um eine Paketquelle zu entfernen, wählen Sie ihn, und wählen Sie dann die **X** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e9b69-177">To remove a package source, select it and then select the **X** button.</span></span>
1. <span data-ttu-id="e9b69-178">Verwenden Sie die nach-oben und nach-unten Sie-Pfeile, um die Prioritätsreihenfolge der Paketquellen überein ändern.</span><span class="sxs-lookup"><span data-stu-id="e9b69-178">Use the up and down arrow buttons to change the priority order of the package sources.</span></span> <span data-ttu-id="e9b69-179">Visual Studio sucht diese Quellen in der Reihenfolge ihrer Priorität beim Wiederherstellen von Paketen für ein Projekt.</span><span class="sxs-lookup"><span data-stu-id="e9b69-179">Visual Studio searches these sources in the priority order when restoring packages for a project.</span></span> <span data-ttu-id="e9b69-180">Weitere Informationen finden Sie unter [paketwiederherstellung](../consume-packages/package-restore.md).</span><span class="sxs-lookup"><span data-stu-id="e9b69-180">For more information, see [Package restore](../consume-packages/package-restore.md).</span></span>

> [!Tip]
> <span data-ttu-id="e9b69-181">Wenn Sie eine Paketquelle erneut angezeigt wird, nach dem Löschen, kann es in einer Computerebene oder Benutzerebene aufgeführt `NuGet.Config` Dateien.</span><span class="sxs-lookup"><span data-stu-id="e9b69-181">If a package source reappears after deleting it, it may be listed in a computer-level or user-level `NuGet.Config` files.</span></span> <span data-ttu-id="e9b69-182">Finden Sie unter [NuGet Konfigurieren von Verhalten](../consume-packages/configuring-nuget-behavior.md) für den Speicherort dieser Dateien, entfernen Sie Sie dann die Quelle, indem Sie die Dateien manuell zu bearbeiten oder die [Nuget Datenquellen Befehl](../tools/nuget-exe-CLI-reference.md).</span><span class="sxs-lookup"><span data-stu-id="e9b69-182">See [Configuring NuGet behavior](../consume-packages/configuring-nuget-behavior.md) for the location of these files, then remove the source by editing the files manually or using the [nuget sources command](../tools/nuget-exe-CLI-reference.md).</span></span>

## <a name="package-manager-options-control"></a><span data-ttu-id="e9b69-183">Paket-Manager-Optionen steuern</span><span class="sxs-lookup"><span data-stu-id="e9b69-183">Package manager Options control</span></span>

<span data-ttu-id="e9b69-184">Wenn ein Paket ausgewählt ist, zeigt der Paket-Manager-UI ein kleines erweiterbare **Optionen** Steuerelement unterhalb der Version-Selektor (hier gezeigten sowohl reduziert und erweitert).</span><span class="sxs-lookup"><span data-stu-id="e9b69-184">When a package is selected, the Package Manager UI displays a small, expandable **Options** control below the version selector (shown here both collapsed and expanded).</span></span> <span data-ttu-id="e9b69-185">Beachten Sie, die für einige Projekt nur Typen der **Vorschaufenster anzeigen** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e9b69-185">Note that for some project types, only the **Show preview window** option is provided.</span></span>

![Optionen des Paket-manager](media/PackageManagerUIOptions.png)

<span data-ttu-id="e9b69-187">Den folgenden Abschnitten werden diese Optionen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-187">The following sections explain these options.</span></span>

### <a name="show-preview-window"></a><span data-ttu-id="e9b69-188">Vorschaufenster anzeigen</span><span class="sxs-lookup"><span data-stu-id="e9b69-188">Show preview window</span></span>

<span data-ttu-id="e9b69-189">Bei Auswahl dieser Option zeigt ein modales Fenster die die Abhängigkeiten eines ausgewählten Pakets vor der Installation des Pakets:</span><span class="sxs-lookup"><span data-stu-id="e9b69-189">When selected, a modal window displays which the dependencies of a chosen package before the package is installed:</span></span>

![Beispiel-Vorschaudialogfeld](media/InstallPreviewDialog.png)

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="install-options"></a>

### <a name="install-and-update-options"></a><span data-ttu-id="e9b69-191">Installations- und Aktualisierungsoptionen</span><span class="sxs-lookup"><span data-stu-id="e9b69-191">Install and Update Options</span></span>

<span data-ttu-id="e9b69-192">(Nicht verfügbar für alle Projekttypen.)</span><span class="sxs-lookup"><span data-stu-id="e9b69-192">(Not available for all project types.)</span></span>

<span data-ttu-id="e9b69-193">**Das abhängigkeitsverhalten** konfiguriert wie NuGet entscheidet sich, welche Versionen der abhängigen Pakete zu installieren:</span><span class="sxs-lookup"><span data-stu-id="e9b69-193">**Dependency behavior** configures how NuGet decides which versions of dependent packages to install:</span></span>

- <span data-ttu-id="e9b69-194">*Ignorieren Sie Abhängigkeiten* überspringt, installieren alle Abhängigkeiten, die zu installierende Paket in der Regel unterbricht.</span><span class="sxs-lookup"><span data-stu-id="e9b69-194">*Ignore dependencies* skips installing any dependencies, which typically breaks the package being installed.</span></span>
- <span data-ttu-id="e9b69-195">*Niedrigste* [Standard] installiert die Abhängigkeit mit der minimalen Versionsnummer, die die Anforderungen des ausgewählten Pakets primären erfüllt.</span><span class="sxs-lookup"><span data-stu-id="e9b69-195">*Lowest* [Default] installs the dependency with the minimal version number that meets the requirements of the primary chosen package.</span></span>
- <span data-ttu-id="e9b69-196">*Höchste Patch* die Version mit der gleichen Haupt-und Nebenversionsnummern Zahlen, aber die höchste Anzahl der Patch installiert.</span><span class="sxs-lookup"><span data-stu-id="e9b69-196">*Highest Patch* installs the version with the same major and minor version numbers, but the highest patch number.</span></span> <span data-ttu-id="e9b69-197">Z. B. wenn Version 1.2.2 angegeben wird die höchste Version, die mit 1.2 beginnt installiert werden</span><span class="sxs-lookup"><span data-stu-id="e9b69-197">For example, if version 1.2.2 is specified then the highest version that starts with 1.2 will be installed</span></span>
- <span data-ttu-id="e9b69-198">*Höchste Nebenversion* die Version mit der gleichen Hauptversionsnummer nur den höchsten Nebenversionsnummer und die Anzahl der Patch installiert.</span><span class="sxs-lookup"><span data-stu-id="e9b69-198">*Highest Minor* installs the version with the same major version number but the highest minor number and patch number.</span></span> <span data-ttu-id="e9b69-199">Wenn Version 1.2.2 angegeben ist, wird die höchste Version, die mit 1 beginnt installiert werden</span><span class="sxs-lookup"><span data-stu-id="e9b69-199">If version 1.2.2 is specified, then the highest version that starts with 1 will be installed</span></span>
- <span data-ttu-id="e9b69-200">*Höchste* installiert die höchste verfügbare Version des Pakets.</span><span class="sxs-lookup"><span data-stu-id="e9b69-200">*Highest* installs the highest available version of the package.</span></span>

<span data-ttu-id="e9b69-201">**Datei Konflikt Aktion** gibt an, wie NuGet Pakete behandeln soll, die bereits im Projekt oder lokalen Computer vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="e9b69-201">**File conflict action** specifies how NuGet should handle packages that already exist in the project or local machine:</span></span>

- <span data-ttu-id="e9b69-202">*Prompt* weist NuGet zu Fragen, ob beibehalten oder überschreiben vorhandene Pakete.</span><span class="sxs-lookup"><span data-stu-id="e9b69-202">*Prompt* instructs NuGet to ask whether to keep or overwrite existing packages.</span></span>
- <span data-ttu-id="e9b69-203">*Ignorieren Sie alle* weist NuGet zum Überschreiben aller vorhandenen Pakete überspringen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-203">*Ignore All* instructs NuGet to skip overwriting any existing packages.</span></span>
- <span data-ttu-id="e9b69-204">*Überschreiben Sie alle* weist NuGet, um vorhandene Pakete zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="e9b69-204">*Overwrite All* instructs NuGet to overwrite any existing packages.</span></span>

<!-- This is here because the link in the UI needs this anchor. See https://github.com/NuGet/NuGet.Client/blob/dev/src/NuGet.Clients/PackageManagement.UI/Xamls/OptionsControl.xaml -->
<a name="uninstall-options"></a>

### <a name="uninstall-options"></a><span data-ttu-id="e9b69-205">Deinstallationsoptionen</span><span class="sxs-lookup"><span data-stu-id="e9b69-205">Uninstall Options</span></span>

<span data-ttu-id="e9b69-206">(Nicht verfügbar für alle Projekttypen.)</span><span class="sxs-lookup"><span data-stu-id="e9b69-206">(Not available for all project types.)</span></span>

<span data-ttu-id="e9b69-207">**Entfernen Sie Abhängigkeiten**: Bei Auswahl dieser Option entfernt alle abhängigen Pakete auf, wenn diese nicht an anderer Stelle im Projekt verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="e9b69-207">**Remove dependencies**: when selected, removes any dependent packages if they're not referenced elsewhere in the project.</span></span>

<span data-ttu-id="e9b69-208">**Deinstallation erzwingen, auch wenn Abhängigkeiten vorhanden sind, darauf**: Bei Auswahl dieser Option wird ein Paket deinstalliert, selbst wenn darauf noch im Projekt verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="e9b69-208">**Force uninstall even if there are dependencies on it**: when selected, uninstalls a package even if it's still being referenced in the project.</span></span> <span data-ttu-id="e9b69-209">Dies wird normalerweise verwendet, in Kombination mit **Abhängigkeiten entfernen** So entfernen Sie ein Paket und alle von Ihnen gewünschten Abhängigkeiten, die es installiert.</span><span class="sxs-lookup"><span data-stu-id="e9b69-209">This is typically used in combination with **Remove dependencies** to remove a package and whatever dependencies it installed.</span></span> <span data-ttu-id="e9b69-210">Mit dieser Option kann jedoch zu fehlerhaften Verweise im Projekt führen.</span><span class="sxs-lookup"><span data-stu-id="e9b69-210">Using this option may, however, lead to broken references in the project.</span></span> <span data-ttu-id="e9b69-211">In solchen Fällen müssen Sie möglicherweise auf [installieren Sie die anderen Pakete](../consume-packages/reinstalling-and-updating-packages.md).</span><span class="sxs-lookup"><span data-stu-id="e9b69-211">In such cases, you may need to [reinstall those other packages](../consume-packages/reinstalling-and-updating-packages.md).</span></span>