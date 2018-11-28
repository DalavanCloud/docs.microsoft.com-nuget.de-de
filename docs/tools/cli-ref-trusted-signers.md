---
title: Vertrauenswürdige Signaturgeber NuGet-CLI-Befehl
description: Referenz für die der vertrauenswürdige Signaturgeber nuget.exe-Befehl
author: patbel
ms.author: patbel
ms.date: 11/12/2018
ms.topic: reference
ms.reviewer: rmpablos
ms.openlocfilehash: ffd0cf5d50a2deed16e1722b32e43047bc81df2f
ms.sourcegitcommit: a1846edf70ddb2505d58e536e08e952d870931b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52303686"
---
# <a name="trusted-signers-command-nuget-cli"></a><span data-ttu-id="2e06a-103">Vertrauenswürdige Signaturgeber-Befehl (NuGet-CLI)</span><span class="sxs-lookup"><span data-stu-id="2e06a-103">trusted-signers command (NuGet CLI)</span></span>

<span data-ttu-id="2e06a-104">**Gilt für:** Paket Verbrauch &bullet; **unterstützte Versionen:** 4.9 und höher</span><span class="sxs-lookup"><span data-stu-id="2e06a-104">**Applies to:** package consumption &bullet; **Supported versions:** 4.9+</span></span>

<span data-ttu-id="2e06a-105">Übernimmt oder bestimmt der vertrauenswürdige Signaturgeber der NuGet-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="2e06a-105">Gets or sets trusted signers to the NuGet configuration.</span></span> <span data-ttu-id="2e06a-106">Zusätzliche Nutzung, finden Sie unter [Konfigurieren des NuGet-Verhaltens](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="2e06a-106">For additional usage, see [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span> <span data-ttu-id="2e06a-107">Weitere Einzelheiten, wie das Schema der Datei "NuGet.config" offenbar, auf die [NuGet Config-Dateiverweis](../reference/nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="2e06a-107">For details on how the nuget.config schema looks like, refer to the [NuGet config file reference](../reference/nuget-config-file.md).</span></span>

## <a name="usage"></a><span data-ttu-id="2e06a-108">Verwendung</span><span class="sxs-lookup"><span data-stu-id="2e06a-108">Usage</span></span>

```cli
nuget trusted-signers <list|add|remove|sync> [options]
```

<span data-ttu-id="2e06a-109">Wenn keine der `list|add|remove|sync` angegeben ist, wird der Befehl standardmäßig `list`.</span><span class="sxs-lookup"><span data-stu-id="2e06a-109">if none of `list|add|remove|sync` is specified, the command will default to `list`.</span></span>

## <a name="nuget-trusted-signers-list"></a><span data-ttu-id="2e06a-110">Liste der NuGet-vertrauenswürdige Signaturgeber</span><span class="sxs-lookup"><span data-stu-id="2e06a-110">nuget trusted-signers list</span></span>

<span data-ttu-id="2e06a-111">Listet alle in der Konfiguration der vertrauenswürdige Signaturgeber.</span><span class="sxs-lookup"><span data-stu-id="2e06a-111">Lists all the trusted signers in the configuration.</span></span> <span data-ttu-id="2e06a-112">Diese Option werden alle Zertifikate enthalten (mit Fingerabdruck und fingerabdruckalgorithmus) jedes Signaturgeber hat.</span><span class="sxs-lookup"><span data-stu-id="2e06a-112">This option will include all the certificates (with fingerprint and fingerprint algorithm) each signer has.</span></span> <span data-ttu-id="2e06a-113">Wenn ein Zertifikat eine vorangestellte verfügt `[U]`, dies bedeutet, dass das Zertifikateintrag hat `allowUntrustedRoot` als `true`.</span><span class="sxs-lookup"><span data-stu-id="2e06a-113">If a certificate has a preceding `[U]`, it means that certificate entry has `allowUntrustedRoot` set as `true`.</span></span>

<span data-ttu-id="2e06a-114">Es folgt eine Beispielausgabe dieses Befehls:</span><span class="sxs-lookup"><span data-stu-id="2e06a-114">Below is an example output from this command:</span></span>

```cli
$ nuget trusted-signers
Registered trusted signers:


 1.   nuget.org [repository]
      Service Index: https://api.nuget.org/v3/index.json
      Certificate fingerprint(s):
        SHA256 - 0E5F38F57DC1BCC806D8494F4F90FBCEDD988B46760709CBEEC6F4219AA6157D

 2.   microsoft [author]
      Certificate fingerprint(s):
        SHA256 - 3F9001EA83C560D712C24CF213C3D312CB3BFF51EE89435D3430BD06B5D0EECE

 3.   myUntrustedAuthorSignature [author]
      Certificate fingerprint(s):
        [U] SHA256 - 518F9CF082C0872025EFB2587B6A6AB198208F63EA58DD54D2B9FF6735CA4434
        
```

## <a name="nuget-trusted-signers-add-options"></a><span data-ttu-id="2e06a-115">Vertrauenswürdige Signaturgeber mit NuGet add [Optionen]</span><span class="sxs-lookup"><span data-stu-id="2e06a-115">nuget trusted-signers add [options]</span></span>

<span data-ttu-id="2e06a-116">Fügt einen vertrauenswürdigen Signaturgeber mit dem angegebenen Namen auf die Konfiguration an. Diese Option hat unterschiedliche Gesten zum Hinzufügen eines vertrauenswürdigen Autor oder Repository.</span><span class="sxs-lookup"><span data-stu-id="2e06a-116">Adds a trusted signer with the given name to the config. This option has different gestures to add a trusted author or repository.</span></span>

## <a name="options-for-add-based-on-a-package"></a><span data-ttu-id="2e06a-117">Optionen zum Hinzufügen, die basierend auf einem Paket</span><span class="sxs-lookup"><span data-stu-id="2e06a-117">Options for add based on a package</span></span>

```cli
nuget trusted-signers add <package(s)> -Name <name> [options]
```

<span data-ttu-id="2e06a-118">wo `<package(s)>` enthält eine oder mehrere `.nupkg` Dateien.</span><span class="sxs-lookup"><span data-stu-id="2e06a-118">where `<package(s)>` is one or more `.nupkg` files.</span></span>

| <span data-ttu-id="2e06a-119">Option</span><span class="sxs-lookup"><span data-stu-id="2e06a-119">Option</span></span> | <span data-ttu-id="2e06a-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2e06a-120">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2e06a-121">Autor</span><span class="sxs-lookup"><span data-stu-id="2e06a-121">Author</span></span> | <span data-ttu-id="2e06a-122">Gibt an, dass die Signatur der Autor der Pakete vertrauenswürdig sind.</span><span class="sxs-lookup"><span data-stu-id="2e06a-122">Specifies that the author signature of the package(s) should be trusted.</span></span> |
| <span data-ttu-id="2e06a-123">Repository</span><span class="sxs-lookup"><span data-stu-id="2e06a-123">Repository</span></span> | <span data-ttu-id="2e06a-124">Gibt an, dass die Repository-Signatur oder die Gegensignatur der Pakete vertrauenswürdig sind.</span><span class="sxs-lookup"><span data-stu-id="2e06a-124">Specifies that the repository signature or countersignature of the package(s) should be trusted.</span></span> |
| <span data-ttu-id="2e06a-125">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="2e06a-125">AllowUntrustedRoot</span></span> | <span data-ttu-id="2e06a-126">Gibt an, wenn das Zertifikat für die der vertrauenswürdige Signaturgeber, eine Verkettung mit einem nicht vertrauenswürdigen Stamm zugelassen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e06a-126">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |
| <span data-ttu-id="2e06a-127">Besitzer</span><span class="sxs-lookup"><span data-stu-id="2e06a-127">Owners</span></span> | <span data-ttu-id="2e06a-128">Durch Semikolons getrennte Liste der vertrauenswürdigen Besitzer, um die Vertrauensstellung eines Repositorys weiter einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="2e06a-128">Semi-colon separated list of trusted owners to further restrict the trust of a repository.</span></span> <span data-ttu-id="2e06a-129">Nur gültig, wenn Sie mit der `-Repository` Option.</span><span class="sxs-lookup"><span data-stu-id="2e06a-129">Only valid when using the `-Repository` option.</span></span> |

<span data-ttu-id="2e06a-130">Bereitstellung `-Author` und `-Repository` zur gleichen Zeit wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2e06a-130">Providing both `-Author` and `-Repository` at the same time is not supported.</span></span>

## <a name="options-for-add-based-on-a-service-index"></a><span data-ttu-id="2e06a-131">Optionen für die basierend auf einem Dienst hinzufügen</span><span class="sxs-lookup"><span data-stu-id="2e06a-131">Options for add based on a service index</span></span>

```cli
nuget trusted-signers add -Name <name> [options]
```

<span data-ttu-id="2e06a-132">_Beachten Sie_: mit dieser Option wird nur vertrauenswürdigen Repositorys hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="2e06a-132">_Note_: This option will only add trusted repositories.</span></span> 

| <span data-ttu-id="2e06a-133">Option</span><span class="sxs-lookup"><span data-stu-id="2e06a-133">Option</span></span> | <span data-ttu-id="2e06a-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2e06a-134">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2e06a-135">ServiceIndex</span><span class="sxs-lookup"><span data-stu-id="2e06a-135">ServiceIndex</span></span> | <span data-ttu-id="2e06a-136">Gibt den Index des V3-Dienst des Repositorys als vertrauenswürdig gelten sollen.</span><span class="sxs-lookup"><span data-stu-id="2e06a-136">Specifies the V3 service index of the repository to be trusted.</span></span> <span data-ttu-id="2e06a-137">Dieses Repository enthält, die die Ressource der Repository-Signaturen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2e06a-137">This repository has to support the repository signatures resource.</span></span> <span data-ttu-id="2e06a-138">Wenn nicht angegeben ist, sieht der Befehl für eine Paketquelle mit dem gleichen `-Name` und dienstindex von dort abrufen.</span><span class="sxs-lookup"><span data-stu-id="2e06a-138">If not provided, the command will look for a package source with the same `-Name` and get the service index from there.</span></span> |
| <span data-ttu-id="2e06a-139">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="2e06a-139">AllowUntrustedRoot</span></span> | <span data-ttu-id="2e06a-140">Gibt an, wenn das Zertifikat für die der vertrauenswürdige Signaturgeber, eine Verkettung mit einem nicht vertrauenswürdigen Stamm zugelassen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e06a-140">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |
| <span data-ttu-id="2e06a-141">Besitzer</span><span class="sxs-lookup"><span data-stu-id="2e06a-141">Owners</span></span> | <span data-ttu-id="2e06a-142">Durch Semikolons getrennte Liste der vertrauenswürdigen Besitzer, um die Vertrauensstellung eines Repositorys weiter einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="2e06a-142">Semi-colon separated list of trusted owners to further restrict the trust of a repository.</span></span> |

## <a name="options-for-add-based-on-the-certificate-information"></a><span data-ttu-id="2e06a-143">Optionen zum Hinzufügen, die basierend auf den Zertifikatinformationen</span><span class="sxs-lookup"><span data-stu-id="2e06a-143">Options for add based on the certificate information</span></span>

```cli
nuget trusted-signers add -Name <name> [options]
```

<span data-ttu-id="2e06a-144">_Beachten Sie_: Wenn es sich bei ein vertrauenswürdiger Signaturgeber mit dem angegebenen Namen bereits vorhanden ist, das zertifikatselement wird hinzugefügt, Signaturgeber.</span><span class="sxs-lookup"><span data-stu-id="2e06a-144">_Note_: If a trusted signer with the given name already exists, the certificate item will be added to that signer.</span></span> <span data-ttu-id="2e06a-145">Andernfalls wird der Autor ein vertrauenswürdigen erstellt werden, mit einem zertifikatselement aus den angegebenen Informationen zum Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="2e06a-145">Otherwise a trusted author will be created with a certificate item from given certificate information.</span></span>

| <span data-ttu-id="2e06a-146">Option</span><span class="sxs-lookup"><span data-stu-id="2e06a-146">Option</span></span> | <span data-ttu-id="2e06a-147">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2e06a-147">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2e06a-148">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="2e06a-148">CertificateFingerprint</span></span> | <span data-ttu-id="2e06a-149">Gibt ein Zertifikat, mit dem Fingerabdrücke der eines Zertifikats, das signierte Pakete signiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2e06a-149">Specifies a certificate fingerprints of a certificate which signed packages must be signed with.</span></span> <span data-ttu-id="2e06a-150">Ein Fingerabdruck des Zertifikats ist ein Hash des Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="2e06a-150">A certificate fingerprint is a hash of the certificate.</span></span> <span data-ttu-id="2e06a-151">Der Hashalgorithmus für die Berechnung des Hash muss gibt an, der `FingerprintAlgorithm` Option.</span><span class="sxs-lookup"><span data-stu-id="2e06a-151">The hash algorithm used for calculating this hash should be specifies in the `FingerprintAlgorithm` option.</span></span> |
| <span data-ttu-id="2e06a-152">FingerprintAlgorithm</span><span class="sxs-lookup"><span data-stu-id="2e06a-152">FingerprintAlgorithm</span></span> | <span data-ttu-id="2e06a-153">Gibt den Hashalgorithmus, der zum Berechnen der Fingerabdruck des Zertifikats an.</span><span class="sxs-lookup"><span data-stu-id="2e06a-153">Specifies the hash algorithm used to calculate the certificate fingerprint.</span></span> <span data-ttu-id="2e06a-154">Wird standardmäßig auf `SHA256` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2e06a-154">Defaults to `SHA256`.</span></span> <span data-ttu-id="2e06a-155">Werte werden unterstützt `SHA256`, `SHA384` und `SHA512`</span><span class="sxs-lookup"><span data-stu-id="2e06a-155">Values supported are `SHA256`, `SHA384` and `SHA512`</span></span> |
| <span data-ttu-id="2e06a-156">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="2e06a-156">AllowUntrustedRoot</span></span> | <span data-ttu-id="2e06a-157">Gibt an, wenn das Zertifikat für die der vertrauenswürdige Signaturgeber, eine Verkettung mit einem nicht vertrauenswürdigen Stamm zugelassen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e06a-157">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |

## <a name="nuget-trusted-signers-remove--name-name"></a><span data-ttu-id="2e06a-158">Entfernen Sie vertrauenswürdige Signaturgeber mit NuGet - Namen <name></span><span class="sxs-lookup"><span data-stu-id="2e06a-158">nuget trusted-signers remove -Name <name></span></span>

<span data-ttu-id="2e06a-159">Entfernt alle vertrauenswürdigen Signaturgeber, die mit dem angegebenen Namen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="2e06a-159">Removes any trusted signers that match the given name.</span></span>

## <a name="nuget-trusted-signers-sync--name-name"></a><span data-ttu-id="2e06a-160">Synchronisieren Sie vertrauenswürdige Signaturgeber mit NuGet - Name <name></span><span class="sxs-lookup"><span data-stu-id="2e06a-160">nuget trusted-signers sync -Name <name></span></span>

<span data-ttu-id="2e06a-161">Fordert die aktuelle Liste der Zertifikate, die im derzeit vertrauenswürdiges Repository verwendet werden, zum Aktualisieren der die vorhandenen Zertifikatliste in der vertrauenswürdige Signaturgeber.</span><span class="sxs-lookup"><span data-stu-id="2e06a-161">Requests the latest list of certificates used in a currently trusted repository to update the the existing certificate list in the trusted signer.</span></span>

<span data-ttu-id="2e06a-162">_Beachten Sie_: dieser Bewegung wird die aktuelle Liste der Zertifikate zu löschen und Ersetzen Sie sie durch eine aktuelle Liste, aus dem Repository.</span><span class="sxs-lookup"><span data-stu-id="2e06a-162">_Note_: This gesture will delete the current list of certificates and replace them with an up-to-date list from the repository.</span></span>

## <a name="options"></a><span data-ttu-id="2e06a-163">Optionen</span><span class="sxs-lookup"><span data-stu-id="2e06a-163">Options</span></span>

| <span data-ttu-id="2e06a-164">Option</span><span class="sxs-lookup"><span data-stu-id="2e06a-164">Option</span></span> | <span data-ttu-id="2e06a-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2e06a-165">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2e06a-166">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="2e06a-166">ConfigFile</span></span> | <span data-ttu-id="2e06a-167">Die NuGet-Konfigurationsdatei angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e06a-167">The NuGet configuration file to apply.</span></span> <span data-ttu-id="2e06a-168">Wenn nicht angegeben, `%AppData%\NuGet\NuGet.Config` (Windows) oder `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e06a-168">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="2e06a-169">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="2e06a-169">ForceEnglishOutput</span></span> | <span data-ttu-id="2e06a-170">Erzwingt, dass nuget.exe über eine invariante Kultur auf Englisch basierenden ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2e06a-170">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="2e06a-171">Help</span><span class="sxs-lookup"><span data-stu-id="2e06a-171">Help</span></span> | <span data-ttu-id="2e06a-172">Zeigt die Informationen für den Befehl Hilfe.</span><span class="sxs-lookup"><span data-stu-id="2e06a-172">Displays help information for the command.</span></span> |
| <span data-ttu-id="2e06a-173">Ausführlichkeit</span><span class="sxs-lookup"><span data-stu-id="2e06a-173">Verbosity</span></span> | <span data-ttu-id="2e06a-174">Gibt an, die Anzahl der Details in der Ausgabe angezeigt: *normalen*, *quiet*, *ausführliche*.</span><span class="sxs-lookup"><span data-stu-id="2e06a-174">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="2e06a-175">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2e06a-175">Examples</span></span>

```cli
nuget trusted-signers list

nuget trusted-signers Add -Name existingSource

nuget trusted-signers Add -Name trustedRepo -ServiceIndex https://trustedRepo.test/v3ServiceIndex

nuget trusted-signers Add -Name author1 -CertificateFingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 -FingerprintAlgorithm SHA256

nuget trusted-signers Add -Repository .\..\MyRepositorySignedPackage.nupkg -Name TrustedRepo

nuget-trusted-signers Remove -Name TrustedRepo

nuget-trusted-signers Sync -Name TrustedRepo
```