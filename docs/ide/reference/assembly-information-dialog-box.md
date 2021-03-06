---
title: Dialogfeld "Assemblyinformationen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae70a2bf989b73dedc5becaac6f4b49bd0108730
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595786"
---
# <a name="assembly-information-dialog-box"></a>Assemblyinformationen (Dialogfeld)

Im Dialogfeld „Assemblyinformationen“ werden die Werte der globalen .NET Framework-Assemblyattribute festgelegt, die in der AssemblyInfo-Datei gespeichert sind, die mit dem Projekt automatisch erstellt wird. Im Projektmappen-Explorer befindet sich die AssemblyInfo-Datei im Knoten **Mein Projekt** für Visual Basic-Projekte (klicken Sie zum Anzeigen auf **Alle Dateien** anzeigen). Für C#-Projekte befindet sie sich unter **Eigenschaften**. Weitere Informationen finden Sie unter [Attribute (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Um auf dieses Dialogfeld zuzugreifen, wählen Sie einen Projektknoten im **Projektmappen-Explorer** aus, und wählen Sie dann im Menü **Projekt** **Eigenschaften**. Auf der Seite **Anwendung** wählen Sie die Schaltfläche **Assemblyinformation**.

## <a name="uielement-list"></a>UIElement-Liste

**Titel**\
Gibt einen Titel für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTitleAttribute>

**Beschreibung**\
Gibt eine optionale Beschreibung für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyDescriptionAttribute>

**Unternehmen**\
Gibt einen Firmennamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCompanyAttribute>

Der Standardwert für das Unternehmen kann in der Registrierung festgelegt oder geändert werden. Suchen Sie nach dem **RegisteredOrganization**-Wert je nach Windowssversion im Schlüssel **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** oder **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**.

**Produkt**\
Gibt einen Produktnamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyProductAttribute>

**Copyright**\
Gibt Copyrightinformationen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCopyrightAttribute>

**Marke**\
Gibt eine Marke für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTrademarkAttribute>

**Assemblyversion**\
Gibt die Version der Assembly an. Entspricht <xref:System.Reflection.AssemblyVersionAttribute>

**Dateiversion**\
Gibt eine Versionsnummer an, die den Compiler anweist, eine bestimmte Version der Versionsressource der Win32-Datei zu verwenden. Entspricht <xref:System.Reflection.AssemblyFileVersionAttribute>

**GUID**\
Eine eindeutige GUID zur Identifizierung der Assembly. Wenn Sie ein Projekt erstellen, generiert Visual Studio eine GUID für die Assembly. Entspricht <xref:System.Guid>

**Neutrale Sprache**\
Gibt an, welche Kultur die Assembly unterstützt. Entspricht <xref:System.Resources.NeutralResourcesLanguageAttribute> Der Standardwert lautet **(Keine)** .

**Assembly COM-sichtbar machen**\
Gibt an, ob Typen in der Assembly für COM verfügbar sind. Entspricht <xref:System.Runtime.InteropServices.ComVisibleAttribute>

> [!NOTE]
> Weitere Informationen zum Festlegen dieser Eigenschaften beim Generieren eines NuGet-Pakets in einer .NET Framework-Klassenbibliothek finden Sie unter [Konfigurieren der Projekteigenschaften für das Paket](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Weitere Informationen

- [Seite "Anwendung", Projekt-Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attribute](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
