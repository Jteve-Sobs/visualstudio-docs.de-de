---
title: '&lt;Zeichenfolgen&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8bc56bf980bba6326b3615b6892ec555b795ec8
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747410"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Zeichenfolgen&gt; -Element (Bootstrapper)
Definiert die lokalisierte Zeichenfolgen für Produktnamen, Paketnamen und Fehlermeldungen für die Installation.

## <a name="syntax"></a>Syntax

```xml
<Strings>
    <String
        Name
    >
    </String>
</Strings>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Die `Strings` Element ist ein untergeordnetes Element des der `Package` Element. Es besitzt keine Attribute.

## <a name="string"></a>Zeichenfolge
 Die `String` Element ist ein untergeordnetes Element des der `Strings` Element. Ein `Strings` Element möglicherweise eine oder mehrere `String` Elemente.

 `String` weist das folgende Attribut an.

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der Name der Zeichenfolge.|

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel gibt alle englischen Zeichenfolgen für den .NET Framework-Installer.

```xml
<Strings>
    <String Name="DisplayName">.NET Framework 2.0</String>
    <String Name="Culture">en</String>
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
</Strings>
```

## <a name="see-also"></a>Siehe auch
- [\<Package >-Element](../deployment/package-element-bootstrapper.md)