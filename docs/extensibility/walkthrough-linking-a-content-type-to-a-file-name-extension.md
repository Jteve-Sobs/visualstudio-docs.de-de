---
title: 'Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4e5ba3cd82090b5fad76d48c4600e0814bd91eb
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904687"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung
Sie können einen eigenen Inhaltstyp definieren und eine Dateinamenerweiterung mit dem Editor-Managed Extensibility Framework (MEF)-Erweiterungen verknüpfen. In einigen Fällen ist die Dateinamenerweiterung bereits durch einen Sprachdienst definiert. Wenn Sie es jedoch mit MEF verwenden möchten, müssen Sie es dennoch mit einem Inhaltstyp verknüpfen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `ContentTypeTest` .

2. Wechseln Sie in der Datei **Source. Extension. vsixmanifest** zur Registerkarte **Objekte** , und legen Sie das Feld **Typ** auf **Microsoft. VisualStudio. MEFComponent**, das Feld **Quelle** auf **ein Projekt in der aktuellen**Projekt Mappe und das **Projekt** Feld auf den Namen des Projekts fest.

## <a name="define-the-content-type"></a>Definieren des Inhaltstyps

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `FileAndContentTypes`.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    1. System.ComponentModel.Composition

    2. Microsoft. VisualStudio. Text. Logic

    3. Microsoft. VisualStudio. coreutility

3. Fügen Sie die folgenden `using` Direktiven hinzu.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Deklarieren Sie eine statische Klasse, die die Definitionen enthält.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. Exportieren Sie in dieser Klasse einen <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> mit dem Namen "HID", und deklarieren Sie die Basis Definition als "Text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Verknüpfen einer Dateinamenerweiterung mit einem Inhaltstyp

- Um diesen Inhaltstyp einer Dateinamenerweiterung zuzuordnen, exportieren Sie eine mit <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> der Erweiterung *. HID* und dem Inhaltstyp "HID".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>Hinzufügen des Inhaltstyps zu einem Editor-Export

1. Erstellen Sie eine Editor-Erweiterung. Sie können z. b. die in Exemplarische Vorgehensweise [: Erstellen eines Rand](../extensibility/walkthrough-creating-a-margin-glyph.md)Symbols beschriebene Rand Symbol Erweiterung verwenden.

2. Fügen Sie die Klasse hinzu, die Sie in dieser Prozedur definiert haben.

3. Fügen Sie beim Exportieren der Erweiterungs Klasse der den <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Typ "HID" hinzu.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Siehe auch
- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
