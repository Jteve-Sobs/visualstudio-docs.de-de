---
title: Gemeinsame MSBuild-Projektelemente | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ed79b1654057c4114ceb171b5cb1e1dfdb439f
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425393"
---
# <a name="common-msbuild-project-items"></a>Gemeinsame MSBuild-Projektelemente

In MSBuild ist ein Element ein benannter Verweis auf eine oder mehrere Dateien. Elemente enthalten Metadaten wie Dateinamen, Pfade und Versionsnummern. Alle Projekttypen in Visual Studio haben mehrere Elemente gemeinsam. Diese Elemente werden in der Datei *Microsoft.Build.CommonTypes.xsd* definiert.

## <a name="common-items"></a>Gemeinsame Elemente

In der folgenden Liste werden alle gemeinsamen Projektelemente aufgeführt.

### <a name="reference"></a>Referenz

Stellt einen Assemblyverweis (verwaltet) im Projekt dar.

|Elementmetadatenname|Beschreibung|
|---------------|-----------------|
|HintPath|Optionale Zeichenfolge. Relativer oder absoluter Pfad der Assembly.|
|name|Optionale Zeichenfolge. Der Anzeigename der Assembly, z. B. "System.Windows.Forms".|
|FusionName|Optionale Zeichenfolge. Gibt den einfachen oder starken Fusionsnamen für das Element an.<br /><br /> Wenn dieses Attribut vorhanden ist, führt dies zu Zeiteinsparungen, da die Assemblydatei zum Abrufen des Fusionsnamens nicht geöffnet werden muss.|
|SpecificVersion|Optionaler boolescher Wert. Gibt an, ob nur auf die Version im Fusionsnamen verwiesen werden soll.|
|Aliase|Optionale Zeichenfolge. Alle Aliase für den Verweis.|
|Private|Optionaler boolescher Wert. Gibt an, ob der Verweis in den Ausgabeordner kopiert werden soll. Dieses Attribut entspricht der Eigenschaft **Lokale Kopie** des Verweises in der Visual Studio-IDE.|

### <a name="comreference"></a>COMReference

Stellt einen COM-Komponentenverweis (nicht verwaltet) im Projekt dar. Dieses Element gilt nur für .NET-Projekte.

|Elementmetadatenname|Beschreibung|
|---------------|-----------------|
|name|Optionale Zeichenfolge. Der Anzeigename der Komponente.|
|GUID|Erforderliche Zeichenfolge. Eine GUID für die Komponente im Format {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Erforderliche Zeichenfolge. Der Hauptteil der Versionsnummer der Komponente. Beispielsweise "5", wenn die Versionsnummer "5.46" lautet.|
|VersionMinor|Erforderliche Zeichenfolge. Der zweite Teil der Versionsnummer (Nebenversionsnummer) der Komponente. Beispielsweise "46", wenn die Versionsnummer "5.46" lautet.|
|LCID|Optionale Zeichenfolge. Die LocaleID (Gebietsschema-ID) für die Komponente.|
|WrapperTool|Optionale Zeichenfolge. Der Name des Wrappertools, das auf die Komponente angewendet wird, z. B. "tlbimp".|
|Isolated|Optionaler boolescher Wert. Gibt an, ob die Komponente eine registrierungsfreie Komponente ist.|

### <a name="comfilereference"></a>COMFileReference

Stellt eine Liste von Typbibliotheken dar, die an den Parameter `TypeLibFiles` des [ResolvedComreference](resolvecomreference-task.md)-Ziels übertragen werden. Dieses Element gilt nur für .NET-Projekte.

|Elementmetadatenname|Beschreibung|
|---------------|-----------------|
|WrapperTool|Optionale Zeichenfolge. Der Name des Wrappertools, das auf die Komponente angewendet wird, z. B. "tlbimp".|

### <a name="nativereference"></a>NativeReference

Stellt eine systemeigene Manifestdatei oder einen Verweis auf eine solche Datei dar.

|Elementmetadatenname|Beschreibung|
|---------------|-----------------|
|name|Erforderliche Zeichenfolge. Der Basisname der Manifestdatei.|
|HintPath|Erforderliche Zeichenfolge. Der relative Pfad der Manifestdatei.|

### <a name="projectreference"></a>ProjectReference

Stellt einen Verweis auf ein anderes Projekt dar. `ProjectReference`-Elemente werden durch das `ResolveProjectReferences`-Ziel in [Verweiselemente](#reference) transformiert. Daher können alle gültigen Metadaten für einen Verweis für `ProjectReference` gültig sein, wenn der Transformationsprozess diese nicht überschreibt.

|Elementmetadatenname|Beschreibung|
|---------------|-----------------|
|name|Optionale Zeichenfolge. Der Anzeigename des Verweises.|
|Projekt|Optionale Zeichenfolge. Eine GUID für den Verweis im Format {12345678-1234-1234-1234-1234567891234}.|
|Package|Optionale Zeichenfolge. Der Pfad der Projektdatei, auf die verwiesen wird.|
|ReferenceOutputAssembly|Optionaler boolescher Wert. Bei Festlegung auf `false` ist die Ausgabe des referenzierten Projekts als [Verweis](#reference) dieses Projekts nicht eingeschlossen, aber dennoch wird sichergestellt, dass das andere Projekt vor diesem Projekt erstellt wird. Wird standardmäßig auf `true` festgelegt.|

### <a name="compile"></a>Compile

Stellt die Quelldateien für den Compiler dar.

| Elementmetadatenname | Beschreibung |
|-----------------------| - |
| DependentUpon | Optionale Zeichenfolge. Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren. |
| AutoGen | Optionaler boolescher Wert. Gibt an, ob die Datei für das Projekt von der integrierten Visual Studio-Entwicklungsumgebung (IDE) generiert wurde. |
| Link | Optionale Zeichenfolge. Der anzuzeigende Notationspfad, wenn sich die Datei physisch außerhalb des Einflusses der Projektdatei befindet. |
| Sichtbar | Optionaler boolescher Wert. Gibt an, ob die Datei im **Projektmappen-Explorer** in Visual Studio angezeigt wird. |
| CopyToOutputDirectory | Optionale Zeichenfolge. Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll. Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

Stellt Ressourcen dar, die in die generierte Assembly eingebettet werden.

| Elementmetadatenname | Beschreibung |
|-----------------------| - |
| DependentUpon | Optionale Zeichenfolge. Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren. |
| Generator | Erforderliche Zeichenfolge. Der Name eines die oft ausgegebene Befehlszeilen  Datei-Generators, der über diesem Element ausgeführt wird. |
| LastGenOutput | Erforderliche Zeichenfolge. Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei-Generator erstellt wurde, der über diesem Element ausgeführt wurde. |
| CustomToolNamespace | Erforderliche Zeichenfolge. Der Namespace, in dem ein beliebiger Datei-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte. |
| Link | Optionale Zeichenfolge. Der Notationspfad wird angezeigt, wenn sich die Datei physisch außerhalb des Einflusses des Projekts befindet. |
| Sichtbar | Optionaler boolescher Wert. Gibt an, ob die Datei im **Projektmappen-Explorer** in Visual Studio angezeigt wird. |
| CopyToOutputDirectory | Optionale Zeichenfolge. Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll. Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest |
| LogicalName | Erforderliche Zeichenfolge. Der logische Name der eingebetteten Ressource. |

### <a name="content"></a>Inhalt

Stellt Dateien dar, die zwar nicht in das Projekt kompiliert werden, jedoch möglicherweise mit dem Projekt eingebettet oder veröffentlicht werden.

| Elementmetadatenname | Beschreibung |
|-----------------------| - |
| DependentUpon | Optionale Zeichenfolge. Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren. |
| Generator | Erforderliche Zeichenfolge. Der Name eines die oft ausgegebene Befehlszeilen  Datei-Generators, der über diesem Element ausgeführt wird. |
| LastGenOutput | Erforderliche Zeichenfolge. Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei-Generator erstellt wurde, der über diesem Element ausgeführt wurde. |
| CustomToolNamespace | Erforderliche Zeichenfolge. Der Namespace, in dem ein beliebiger Datei-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte. |
| Link | Optionale Zeichenfolge. Der anzuzeigende Notationspfad, wenn sich die Datei physisch außerhalb des Einflusses des Projekts befindet. |
| PublishState | Erforderliche Zeichenfolge. Der Inhalt kann einen der folgenden Veröffentlichungszustände aufweisen:<br /><br /> –  Default (Standard)<br />–   Included (Enthalten)<br />–   Excluded (Ausgeschlossen)<br />–   DataFile<br />–   Prerequisite (Voraussetzung) |
| IsAssembly | Optionaler boolescher Wert. Gibt an, ob die Datei eine Assembly ist. |
| Sichtbar | Optionaler boolescher Wert. Gibt an, ob die Datei im **Projektmappen-Explorer** in Visual Studio angezeigt wird. |
| CopyToOutputDirectory | Optionale Zeichenfolge. Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll. Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest |

### <a name="none"></a>Keine

Stellt Dateien dar, die keine Rolle im Buildprozess haben sollen.

| Elementmetadatenname | Beschreibung |
|-----------------------| - |
| DependentUpon | Optionale Zeichenfolge. Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren. |
| Generator | Erforderliche Zeichenfolge. Der Name eines die oft ausgegebene Befehlszeilen  Datei-Generators, der über diesem Element ausgeführt wird. |
| LastGenOutput | Erforderliche Zeichenfolge. Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei-Generator erstellt wurde, der über diesem Element ausgeführt wurde. |
| CustomToolNamespace | Erforderliche Zeichenfolge. Der Namespace, in dem ein beliebiger Datei-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte. |
| Link | Optionale Zeichenfolge. Der anzuzeigende Notationspfad, wenn sich die Datei physisch außerhalb des Einflusses des Projekts befindet. |
| Sichtbar | Optionaler boolescher Wert. Gibt an, ob die Datei im **Projektmappen-Explorer** in Visual Studio angezeigt wird. |
| CopyToOutputDirectory | Optionale Zeichenfolge. Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll. Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

Stellt Assemblyattribute dar, die als `[AssemblyMetadata(key, value)]` generiert werden sollen.

| Elementmetadatenname | Beschreibung |
|-----------------------| - |
| Einschließen | Wird zum ersten Parameter (Schlüssel) im Attributkonstruktor `AssemblyMetadataAttribute`. |
| Wert | Erforderliche Zeichenfolge. Wird zum zweiten Parameter (Wert) im Attributkonstruktor `AssemblyMetadataAttribute`. |

> [!NOTE]
> Dies gilt nur für Projekte, die das .NET Core SDK verwenden.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Stellt das Basisanwendungsmanifest für den Build dar und enthält Sicherheitsinformationen für die ClickOnce-Bereitstellung.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

Stellt das zu importierende FxCop-Projekt dar.

### <a name="import"></a>Importieren

Stellt Assemblys dar, deren Namespaces vom Visual Basic-Compiler importiert werden sollen.

## <a name="see-also"></a>Siehe auch

- [Gemeinsame MSBuild-Projekteigenschaften](../msbuild/common-msbuild-project-properties.md)
- [MSBuild-Eigenschaften für .NET Core SDK-Projekte](/dotnet/core/project-sdk/msbuild-props)
- [Gemeinsame MSBuild-Elementmetadaten](common-msbuild-item-metadata.md)