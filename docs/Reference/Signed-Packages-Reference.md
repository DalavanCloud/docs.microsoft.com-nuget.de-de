---
title: Signierte Pakete-Referenz | Microsoft Docs
author: rido-min
ms.author: rido-min
manager: unniravindranathan
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: Signierte Pakete funktionsbeschreibung.
keywords: NuGet-Paket-Anmeldung, Signatur, Zertifikat
ms.reviewer:
- ananguar
- karann-msft
- unniravindranathan
ms.openlocfilehash: 4763b0dde0153f9e8ea840d5e788b5a3d96b9bd8
ms.sourcegitcommit: 8f26d10bdf256f72962010348083ff261dae81b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="signed-packages"></a>Signierte Pakete

*NuGet-4.6.0+ und Visual Studio 2017 15.6 und höher*

NuGet-Pakete können es sich um eine digitale Signatur einzuschließen, die Schutz vor manipulierte Inhalte enthält. Diese Signatur wird aus einem x. 509-Zertifikat erzeugt, die der tatsächliche Ursprung der das Paket auch Authentizität Proofs hinzufügt.

Signierte Pakete bereitstellen die stärkste End-to-End-Überprüfung. Eine Autor-Signatur wird sichergestellt, dass das Paket nicht geändert wurde, seit der Autor das Paket, unabhängig davon aus signiert die Repositorys oder welche Methode transport das Paket wird übermittelt.

Kunden, die eine gesperrtes-Umgebung "demand" können mit einem bestimmten Autor-Zertifikat signierte Pakete erfordern.

Darüber hinaus bieten Autor signierte Pakete einen zusätzlichen Authentifizierungsmechanismus die publishing nuget.org-Pipeline, da das Signaturzertifikat voraus registriert werden muss.

Weitere Informationen zum Erstellen eines signierten Pakets, finden Sie unter [Signieren von Paketen](../create-packages/Sign-a-package.md) und [NuGet-Anmelde-Befehls](../tools/cli-ref-sign.md).

> [!Important]
> NuGet.org akzeptiert gegenwärtig nicht signierte Pakete. Sie können Pakete für das Veröffentlichen von benutzerdefinierten Feeds signieren.

## <a name="certificate-requirements"></a>Zertifikatanforderungen

Codesignaturzertifikat anfordern, die eine besondere Art von Zertifikat ist, die für gültig ist paketsignierung erfordert die `id-kp-codeSigning` Zweck [[RFC 5280 Abschnitt 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)]. Darüber hinaus muss das Zertifikat eine RSA Länge des öffentliche Schlüssels von 2048 Bits oder höher aufweisen.

## <a name="get-a-code-signing-certificate"></a>Erhalten Sie ein Codesignaturzertifikat

Gültige Zertifikate können von öffentlichen Zertifizierungsstellen wie abgerufen werden:

- [Symantec](https://trustcenter.websecurity.symantec.com/process/trust/productOptions?productType=SoftwareValidationClass3)
- [DigiCert](https://www.digicert.com/code-signing/)
- [Go Daddy](https://www.godaddy.com/web-security/code-signing-certificate)
- [Globale anmelden](https://www.globalsign.com/en/code-signing-certificate/)
- [Comodo](https://www.comodo.com/e-commerce/code-signing/code-signing-certificate.php)
- [Certum](https://www.certum.eu/certum/cert,offer_en_open_source_cs.xml) 

Die vollständige Liste der Zertifizierungsstellen von Windows als vertrauenswürdig eingestuft erhalten von [http://aka.ms/trustcertpartners](http://aka.ms/trustcertpartners).

## <a name="create-a-test-certificate"></a>Ein Testzertifikat erstellen

Sie können selbst ausgestellte Zertifikate für Testzwecke verwenden. Verwenden Sie zum Erstellen eines selbst ausgegebenen Zertifikats die [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate) PowerShell-Befehl.

```ps
New-SelfSignedCertificate -Subject "CN=NuGet Test Developer, OU=Use for testing purposes ONLY" `
                          -FriendlyName "NuGetTestDeveloper" `
                          -Type CodeSigning `
                          -KeyUsage DigitalSignature `
                          -KeyLength 2048 `
                          -KeyAlgorithm RSA `
                          -HashAlgorithm SHA256 `
                          -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
                          -CertStoreLocation "Cert:\CurrentUser\My" 
```

Dieser Befehl erstellt ein Testzertifikats verfügbar im persönlichen Zertifikatspeicher des aktuellen Benutzers. Sie können den Zertifikatspeicher öffnen, indem ausgeführt `certmgr.msc` des neu erstellten Zertifikats angezeigt.

## <a name="timestamp-requirements"></a>Timestamp-Anforderungen

Signierte Pakete sollten einen RFC 3161-Zeitstempel Sicherstellen der Gültigkeit der Signatur außerhalb der Gültigkeitsdauer des Zertifikats signieren Paket enthalten. Das Zertifikat zum Signieren des Zeitstempels muss gültig sein kann die `id-kp-timeStamping` Zweck [[RFC 5280 Abschnitt 4.2.1.12](https://tools.ietf.org/html/rfc5280#section-4.2.1.12)]. Darüber hinaus muss das Zertifikat eine RSA Länge des öffentliche Schlüssels von 2048 Bits oder höher aufweisen.

Zusätzliche technische Details finden Sie der [Paket Signatur technische Spezifikationen](https://github.com/NuGet/Home/wiki/Package-Signatures-Technical-Details) (GitHub).