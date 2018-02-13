---
title: "Archivinhalte zu „project.json“ in NuGet | Microsoft-Dokumentation"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 01/17/2018
ms.topic: article
ms.prod: nuget
ms.technology: 
description: "Sonstige Bestandteile von Inhalten zu „project.json“, die aus anderen Bereichen der NuGet-Dokumentation entfernt wurden."
keywords: "Die Datei „project.json“ in NuGet"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 42a40c6c637839c13effc9e476ac5702a92cfd2a
ms.sourcegitcommit: 4651b16a3a08f6711669fc4577f5d63b600f8f58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="projectjson-archive"></a><span data-ttu-id="6725c-104">project.json-Archiv</span><span class="sxs-lookup"><span data-stu-id="6725c-104">project.json archive</span></span>

<span data-ttu-id="6725c-105">Das Verweisformat `project.json` wurde mit NuGet 3.x eingeführt und wird für bestimmte Projekttypen verwendet.</span><span class="sxs-lookup"><span data-stu-id="6725c-105">The `project.json` reference format was introduced with NuGet 3.x and used for certain project types.</span></span> <span data-ttu-id="6725c-106">Mit der Einführung des PackageReference-Formats, in dem Abhängigkeiten direkt in einer Projektdatei aufgelistet werden, ist es veraltet.</span><span class="sxs-lookup"><span data-stu-id="6725c-106">It was deprecated with the introduction of the PackageReference format, in which dependencies are listed directly in a project file.</span></span>

<span data-ttu-id="6725c-107">Siehe auch:</span><span class="sxs-lookup"><span data-stu-id="6725c-107">Also see:</span></span>

- [<span data-ttu-id="6725c-108">project.json-Schema</span><span class="sxs-lookup"><span data-stu-id="6725c-108">project.json schema</span></span>](project-json.md)
- [<span data-ttu-id="6725c-109">project.json impact on package authors (Auswirkungen von project.json auf Paketersteller)</span><span class="sxs-lookup"><span data-stu-id="6725c-109">project.json impact on package authors</span></span>](project-json-impact.md)
- [<span data-ttu-id="6725c-110">„project.json“ und UWP</span><span class="sxs-lookup"><span data-stu-id="6725c-110">project.json and UWP</span></span>](project-json-and-uwp.md)

## <a name="projectjson-reference-format"></a><span data-ttu-id="6725c-111">project.json-Verweisformat</span><span class="sxs-lookup"><span data-stu-id="6725c-111">project.json reference format</span></span>

<span data-ttu-id="6725c-112">*Ursprünglich unter [Paketwiederherstellung](../what-is-nuget.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-112">*Originally in [Package restore](../what-is-nuget.md).*</span></span>

<span data-ttu-id="6725c-113">In der Liste der Formate von Verweisen:</span><span class="sxs-lookup"><span data-stu-id="6725c-113">In the list of reference formats:</span></span>

- <span data-ttu-id="6725c-114">[`project.json`](project-json.md): *(veraltet)* Eine JSON-Datei, die eine Liste der Projektabhängigkeiten mit einem allgemeinen Paketdiagramm in einer verknüpften Datei `project.lock.json` verwaltet.</span><span class="sxs-lookup"><span data-stu-id="6725c-114">[`project.json`](project-json.md): *(deprecated)* A JSON file that maintains a list of the project's dependencies with an overall package graph in an associated file, `project.lock.json`.</span></span> <span data-ttu-id="6725c-115">Dieses Format ist veraltet und wurde durch PackageReference ersetzt.</span><span class="sxs-lookup"><span data-stu-id="6725c-115">This format is deprecated in favor of PackageReference.</span></span>

## <a name="nuget-restore-on-mono"></a><span data-ttu-id="6725c-116">„nuget restore“ in Mono</span><span class="sxs-lookup"><span data-stu-id="6725c-116">nuget restore on Mono</span></span>

<span data-ttu-id="6725c-117">*Ursprünglich unter [Installieren von NuGet-Clienttools](../install-nuget-client-tools.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-117">*Originally in [Install NuGet client tools](../install-nuget-client-tools.md).*</span></span>

<span data-ttu-id="6725c-118">Funktioniert mit `project.json`.</span><span class="sxs-lookup"><span data-stu-id="6725c-118">Works with `project.json`.</span></span>

## <a name="constraining-package-versions-with-restore"></a><span data-ttu-id="6725c-119">Einschränken der Paketversionen mit der Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="6725c-119">Constraining package versions with restore</span></span>

<span data-ttu-id="6725c-120">*Ursprünglich unter [Paketwiederherstellung](../consume-packages/package-restore.md#constraining-package-versions-with-restore).*</span><span class="sxs-lookup"><span data-stu-id="6725c-120">*Originally in [Package restore](../consume-packages/package-restore.md#constraining-package-versions-with-restore).*</span></span>

- <span data-ttu-id="6725c-121">`project.json`: Gibt einen Versionsbereich zusammen mit der Versionsnummer der Abhängigkeit an.</span><span class="sxs-lookup"><span data-stu-id="6725c-121">`project.json`: Specify a version range directly with the dependency's version number.</span></span> <span data-ttu-id="6725c-122">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="6725c-122">For example:</span></span>

    ```json
    "Newtonsoft.json": "[6, 7)"
    ```

## <a name="nuget-cli-commands"></a><span data-ttu-id="6725c-123">NuGet-CLI-Befehle</span><span class="sxs-lookup"><span data-stu-id="6725c-123">NuGet CLI commands</span></span>

- <span data-ttu-id="6725c-124">`nuget install` funktioniert nicht mit `project.json`.</span><span class="sxs-lookup"><span data-stu-id="6725c-124">`nuget install` does not work with `project.json`.</span></span>
- <span data-ttu-id="6725c-125">`nuget restore`: erstellt bei Projekten, die `project.json` verwenden, die Dateien `project.lock.json` und `<project>.nuget.props` (wenn nötig).</span><span class="sxs-lookup"><span data-stu-id="6725c-125">`nuget restore`: with projects using `project.json`, generates a `project.lock.json` file and a `<project>.nuget.props` file, if needed.</span></span> <span data-ttu-id="6725c-126">(Beide Dateien können aus der Quellcodeverwaltung ausgelassen werden.) Das Argument `<projectPath>` kann auf eine `project.json`-Datei verweisen und hat das gleiche Verhalten wie das Verweisen auf eine `packages.config`-Datei oder eine Projektdatei.</span><span class="sxs-lookup"><span data-stu-id="6725c-126">(Both files can be omitted from source control.) The `<projectPath>` argument can point a `project.json` file and has the same behavior as pointing to a `packages.config` or project file.</span></span> <span data-ttu-id="6725c-127">Nach der Reihenfolge für die Priorität von Paketordnern wird zuerst nach `%userprofile%\.nuget\packages` gesucht, wenn `project.json` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6725c-127">In the priority order for package folders, `%userprofile%\.nuget\packages` is searched first when using `project.json`.</span></span>
- <span data-ttu-id="6725c-128">`nuget update`: Unter Mono funktioniert dieser Befehl nicht bei Projekten, die `project.json` verwenden.</span><span class="sxs-lookup"><span data-stu-id="6725c-128">`nuget update`: On Mono, this command does not work with projects using `project.json`.</span></span>

## <a name="dependency-resolution-with-packagereference"></a><span data-ttu-id="6725c-129">Abhängigkeitsauflösung mit PackageReference</span><span class="sxs-lookup"><span data-stu-id="6725c-129">Dependency resolution with PackageReference</span></span>

<span data-ttu-id="6725c-130">*Ursprünglich unter [Abhängigkeitsauflösung](../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference).*</span><span class="sxs-lookup"><span data-stu-id="6725c-130">*Originally in [Dependency resolution](../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference).*</span></span>

<span data-ttu-id="6725c-131">Dieses Verhalten von PackageReference gilt auch für `project.json`.</span><span class="sxs-lookup"><span data-stu-id="6725c-131">The behavior of PackageReference applies also to `project.json`.</span></span> <span data-ttu-id="6725c-132">„nuget restore“ schreibt das Abhängigkeitsdiagramm in eine Datei namens `project.lock.json` zusammen mit `project.json`.</span><span class="sxs-lookup"><span data-stu-id="6725c-132">NuGet restore writes the dependency graph into a file named `project.lock.json` alongside `project.json`.</span></span>

## <a name="managing-dependency-assets"></a><span data-ttu-id="6725c-133">Verwalten von Abhängigkeitsobjekten</span><span class="sxs-lookup"><span data-stu-id="6725c-133">Managing dependency assets</span></span>

<span data-ttu-id="6725c-134">*Ursprünglich unter [Abhängigkeitsauflösung](../consume-packages/dependency-resolution.md#managing-dependency-assets).*</span><span class="sxs-lookup"><span data-stu-id="6725c-134">*Originally in [Dependency resolution](../consume-packages/dependency-resolution.md#managing-dependency-assets).*</span></span>

<span data-ttu-id="6725c-135">Wenn Sie das Format `project.json` verwenden, können Sie kontrollieren, welche Objekte aus den Abhängigkeiten in die allgemeinen Projekte fließen.</span><span class="sxs-lookup"><span data-stu-id="6725c-135">When using the `project.json` format, you can control which assets from dependencies flow into the top-level project.</span></span> <span data-ttu-id="6725c-136">Weitere Informationen finden Sie unter [project.json](project-json.md).</span><span class="sxs-lookup"><span data-stu-id="6725c-136">For details, see [project.json](project-json.md).</span></span>

## <a name="excluding-references"></a><span data-ttu-id="6725c-137">Ausschließen von Verweisen</span><span class="sxs-lookup"><span data-stu-id="6725c-137">Excluding references</span></span>

<span data-ttu-id="6725c-138">*Ursprünglich unter [Abhängigkeitsauflösung](../consume-packages/dependency-resolution.md#excluding-references).*</span><span class="sxs-lookup"><span data-stu-id="6725c-138">*Originally in [Dependency resolution](../consume-packages/dependency-resolution.md#excluding-references).*</span></span>

- <span data-ttu-id="6725c-139">`project.json`: Fügen Sie `"exclude" : "all"` in der Abhängigkeit für Paket C hinzu:</span><span class="sxs-lookup"><span data-stu-id="6725c-139">`project.json`: add `"exclude" : "all"` in the dependency for PackageC:</span></span>

    ```json
    {
        "dependencies": {
            "PackageC": {
            "version": "1.0.0",
            "exclude": "all"
            }
        }
    }
    ```

## <a name="resolving-incompatible-package-errors"></a><span data-ttu-id="6725c-140">Auflösen von inkompatiblen Paketfehlern</span><span class="sxs-lookup"><span data-stu-id="6725c-140">Resolving incompatible package errors</span></span>

<span data-ttu-id="6725c-141">*Ursprünglich unter [Abhängigkeitsauflösung](../consume-packages/dependency-resolution.md#resolving-incompatible-package-errors).*</span><span class="sxs-lookup"><span data-stu-id="6725c-141">*Originally in [Dependency resolution](../consume-packages/dependency-resolution.md#resolving-incompatible-package-errors).*</span></span>

<span data-ttu-id="6725c-142">Eine zusätzliche Möglichkeit zum Beheben von Fehlern:</span><span class="sxs-lookup"><span data-stu-id="6725c-142">An added means of resolving errors:</span></span>

- <span data-ttu-id="6725c-143">**Nicht empfohlen:** Während Sie mit dem Paketautor zusammenarbeiten, können auch Projekte für `netcore`, `netstandard` und `netcoreapp` andere Frameworks als kompatibel angeben. So können auch Pakete für andere Frameworks verwendet werden. Dies ist aber nur eine temporäre Lösung.</span><span class="sxs-lookup"><span data-stu-id="6725c-143">**Not recommended**: as a temporary solution while you work with the package author, projects targeting `netcore`, `netstandard`, and `netcoreapp` can denote other frameworks as being compatible, thereby allowing packages targeting those other frameworks to be used.</span></span> <span data-ttu-id="6725c-144">Informationen dazu finden Sie unter [project.json imports (Importe von „project.json“)](project-json.md#imports) und [MSBuild restore target PackageTargetFallback (MSBuild-Wiederherstellungsziel „PackageTargetFallback“)](../reference/msbuild-targets.md#packagetargetfallback).</span><span class="sxs-lookup"><span data-stu-id="6725c-144">See [project.json imports](project-json.md#imports) and [MSBuild restore target PackageTargetFallback](../reference/msbuild-targets.md#packagetargetfallback).</span></span> <span data-ttu-id="6725c-145">Dieser Vorgang kann unerwartetes Verhalten hervorrufen. Daher ist es besser, Paketinkompatibilitäten aufzulösen, indem Sie zusammen mit dem Paketautor ein Update entwickeln.</span><span class="sxs-lookup"><span data-stu-id="6725c-145">This can cause unexpected behaviors, so again, it's best to resolve package incompatibilities by working with the package author on an update.</span></span>

## <a name="target-frameworks"></a><span data-ttu-id="6725c-146">Zielframeworks</span><span class="sxs-lookup"><span data-stu-id="6725c-146">Target frameworks</span></span>

<span data-ttu-id="6725c-147">*Ursprünglich unter [Zielframework](../reference/target-frameworks.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-147">*Originally in [Target frameworks](../reference/target-frameworks.md).*</span></span>

- <span data-ttu-id="6725c-148">[project.json:](project-json.md) Der `frameworks`-Knoten gibt die Frameworkversionen an, für die das Projekt kompiliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6725c-148">[project.json](project-json.md): The `frameworks` node specifies the framework versions that the project can be compiled against.</span></span>

## <a name="creating-a-package"></a><span data-ttu-id="6725c-149">Erstellen eines Pakets</span><span class="sxs-lookup"><span data-stu-id="6725c-149">Creating a package</span></span>

<span data-ttu-id="6725c-150">*Ursprünglich unter [Erstellen eines Pakets](../create-packages/creating-a-package.md)*</span><span class="sxs-lookup"><span data-stu-id="6725c-150">*Originally in [Creating a package](../create-packages/creating-a-package.md)*</span></span>

### <a name="setting-a-package-type"></a><span data-ttu-id="6725c-151">Festlegen eines Pakettyps</span><span class="sxs-lookup"><span data-stu-id="6725c-151">Setting a package type</span></span>

<span data-ttu-id="6725c-152">Wenn bei .NET Core 1.x ein DotnetCliTool-Paket installiert wurde, fügt Visual Studio das Paket in den Knoten `project.json` `tools` ein, anstelle des Knotens `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="6725c-152">With .NET Core 1.x, when a DotnetCliTool package is installed, Visual Studio places the package in the `project.json` `tools` node instead of the `dependencies` node.</span></span>

<span data-ttu-id="6725c-153">Pakettypen werden in der Datei `project.json` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6725c-153">Package types are set in `project.json`.</span></span>

- <span data-ttu-id="6725c-154">`project.json`: Geben Sie den Pakettyp innerhalb einer JSON-formatierten `packOptions.packageType`-Eigenschaft an:</span><span class="sxs-lookup"><span data-stu-id="6725c-154">`project.json`: Indicate the package type within a `packOptions.packageType` property json:</span></span>

    ```json
    {
        // ...
        "packOptions": {
        "packageType": "DotnetCliTool"
        }
    }
    ```

### <a name="adding-targets-and-props-for-msbuild"></a><span data-ttu-id="6725c-155">Hinzufügen von Zielen und Eigenschaften für MSBuild</span><span class="sxs-lookup"><span data-stu-id="6725c-155">Adding targets and props for MSBuild</span></span>

<span data-ttu-id="6725c-156">*Ursprünglich unter [Erstellen von .NET Standard-NuGet-Paketen mit Visual Studio 2015](../guides/create-net-standard-packages-vs2015.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-156">*Originally in [Create .NET Standard NuGet Packages with Visual Studio 2015](../guides/create-net-standard-packages-vs2015.md).*</span></span>

<span data-ttu-id="6725c-157">Wenn Sie `project.json` verwenden, werden Ziele nicht zum Projekt hinzugefügt, sondern über `project.lock.json` zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="6725c-157">When using `project.json`, targets are not added to the project but are made available through the `project.lock.json`.</span></span>

### <a name="package-versioning"></a><span data-ttu-id="6725c-158">Paketversionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="6725c-158">Package versioning</span></span>

<span data-ttu-id="6725c-159">*Ursprünglich unter [Paketversionsverwaltung](../reference/package-versioning.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-159">*Originally in [Package versioning](../reference/package-versioning.md).*</span></span>

<span data-ttu-id="6725c-160">Wenn das Format `project.json` verwendet wird, unterstützt NuGet auch die Verwendung eines Platzhalterzeichens \* für den Suffix der Zahl bei Haupt-, Neben-, Patch- und Vorabversionen.</span><span class="sxs-lookup"><span data-stu-id="6725c-160">When using the `project.json` format, NuGet also supports using a wildcard notation, \*, for Major, Minor, Patch, and pre-release suffix parts of the number.</span></span>

### <a name="nugetconfig-reference"></a><span data-ttu-id="6725c-161">Verweis auf „NuGet.Config“</span><span class="sxs-lookup"><span data-stu-id="6725c-161">NuGet.Config reference</span></span>

<span data-ttu-id="6725c-162">*Ursprünglich unter [Verweis auf „NuGet.Config“](../reference/nuget-config-file.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-162">*Originally in [NuGet.Config reference](../reference/nuget-config-file.md).*</span></span>

<span data-ttu-id="6725c-163">`globalPackagesFolder` gilt nur für `project.json`.</span><span class="sxs-lookup"><span data-stu-id="6725c-163">`globalPackagesFolder` applies only to `project.json`.</span></span>

### <a name="nuspec-file-reference"></a><span data-ttu-id="6725c-164">NUSPEC-Dateiverweis</span><span class="sxs-lookup"><span data-stu-id="6725c-164">nuspec file reference</span></span>

<span data-ttu-id="6725c-165">*Ursprünglich unter [NUSPEC-Verweis](../reference/nuspec.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-165">*Originally in [nuspec reference](../reference/nuspec.md).*</span></span>

<span data-ttu-id="6725c-166">Anstelle von `<files>` wird das Element `<contentFiles>` mit `project.json` verwendet.</span><span class="sxs-lookup"><span data-stu-id="6725c-166">The `<contentFiles>` element is used instead of `<files>` with `project.json`.</span></span>

### <a name="package-manager-options-control"></a><span data-ttu-id="6725c-167">Steuerelement „Optionen“ im Paket-Manager</span><span class="sxs-lookup"><span data-stu-id="6725c-167">Package manager options control</span></span>

<span data-ttu-id="6725c-168">*Ursprünglich unter [Referenz zur Benutzeroberfläche des Paket-Managers](../tools/package-manager-ui.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-168">*Originally in [Package Manager UI reference](../tools/package-manager-ui.md).*</span></span>

<span data-ttu-id="6725c-169">Projekte, die das Verweisformat `project.json` verwenden zeigen nur die Option **Vorschaufenster anzeigen** an.</span><span class="sxs-lookup"><span data-stu-id="6725c-169">Projects using `project.json` reference format show only the **Show preview window** option.</span></span>

### <a name="visual-studio-templates"></a><span data-ttu-id="6725c-170">Visual Studio-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="6725c-170">Visual Studio Templates</span></span>

<span data-ttu-id="6725c-171">*Ursprünglich unter [NuGet-Pakete in Visual Studio-Vorlagen](../visual-studio-extensibility/visual-studio-templates.md).*</span><span class="sxs-lookup"><span data-stu-id="6725c-171">*Originally in [NuGet Packages in Visual Studio templates](../visual-studio-extensibility/visual-studio-templates.md).*</span></span>

<span data-ttu-id="6725c-172">Bewährte Methoden: Vorlagen enthalten keine `project.json`-Datei, und enthalten keinerlei Verweise oder Inhalt, die bei der Installation von NuGet-Paketen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="6725c-172">Best practices: templates do not include a `project.json` file, and do not include or any references or content that would be added when NuGet packages are installed.</span></span>