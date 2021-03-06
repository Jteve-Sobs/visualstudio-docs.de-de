---
title: Anzeigen von Zeichenfolgen in einer Zeichenfolgenschnellansicht | Microsoft-Dokumentation
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33e1cbd4b1c754498d7e2bd6c354e874ae8cdad5
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450397"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Anzeigen von Zeichenfolgen in einer Zeichenfolgenschnellansicht in Visual Studio

Beim Debuggen in Visual Studio können Sie Zeichenfolgen mit der integrierten Zeichenfolgenschnellansicht anzeigen. In der Zeichenfolgenschnellansicht werden Zeichenfolgen angezeigt, die zu lang für einen Datentipp oder ein Debuggerfenster sind. Sie kann auch dabei helfen, falsch formatierte Zeichenfolgen zu ermitteln.

Die integrierte Zeichenfolgenschnellansicht beinhaltet Optionen für Nur-Text, XML, HTML und JSON. Über das Fenster **Auto** oder andere Debuggerfenster können Sie auch integrierte Schnellansichten für einige andere Typen (z. B. [DataSet-, DataTable- und DataView-Objekte](../debugger/dataset-visualizer-dialog-box.md)) öffnen.

> [!NOTE]
> Informationen zum Überprüfen von XAML- oder WPF-Benutzeroberflächenelemente in einer Schnellansicht finden Sie unter [Überprüfen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md) oder [Verwenden der WPF-Strukturschnellansicht](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Öffnen einer Zeichenfolgenschnellansicht

Das Debuggen muss pausiert sein, wenn Sie die Zeichenfolgenschnellansicht öffnen möchten. Zeigen Sie auf eine Variable mit einem Nur-Text-, XML-, HTML- oder JSON-Zeichenfolgenwert, und wählen Sie das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht") aus.

![Öffnen einer Zeichenfolgenschnellansicht](../debugger/media/dbg-tips-string-visualizers.png "Öffnen der Zeichenfolgenschnellansicht")

## <a name="view-string-visualizer-data"></a>Anzeigen der Daten einer Zeichenfolgenschnellansicht

Im Fenster der Zeichenfolgenschnellansicht wird im Feld **Ausdruck** die Variable oder der Ausdruck angezeigt, auf die bzw. den Sie zeigen. Das Feld **Wert** enthält den Zeichenfolgenwert.

Ist **Wert** leer, bedeutet das, dass die ausgewählte Schnellansicht die Zeichenfolge nicht erkennen kann. In der **XML-Schnellansicht** wird beispielsweise ein leerer **Wert** für eine Textzeichenfolge ohne XML-Tags oder für eine JSON-Zeichenfolge angezeigt.

Wählen Sie die **Text-Schnellansicht** aus, um Zeichenfolgen anzuzeigen, die von der ausgewählten Schnellansicht nicht erkannt werden. Von der **Text-Schnellansicht** wird Nur-Text angezeigt.

### <a name="view-json-string-data"></a>Anzeigen von JSON-Zeichenfolgendaten

Eine wohlgeformte JSON-Zeichenfolge ähnelt der unten gezeigten Abbildung in der JSON-Schnellansicht. Für eine falsch formatierte JSON-Zeichenfolge wird unter Umständen ein Fehlersymbol (oder bei Nichterkennung ein leerer Wert) angezeigt. Kopieren Sie die Zeichenfolge, und fügen Sie sie in ein Tool für JSON-Linting (etwa [JSLint](https://www.jslint.com/)) ein, um den JSON-Fehler zu identifizieren.

![JSON-Zeichenfolgenschnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichenfolgenschnellansicht")

### <a name="view-xml-string-data"></a>Anzeigen von XML-Zeichenfolgendaten

Eine wohlgeformte XML-Zeichenfolge ähnelt der unten gezeigten Abbildung in der XML-Schnellansicht. Eine falsch formatierte XML-Zeichenfolge wird möglicherweise ohne XML-Tags oder bei Nichterkennung als leerer Wert angezeigt.

![XML-Zeichenfolgenschnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichenfolgenschnellansicht")

### <a name="view-html-string-data"></a>Anzeigen von HTML-Zeichenfolgendaten

Eine wohlgeformte HTML-Zeichenfolge wird wie beim Rendern im Browser angezeigt, wie in der folgenden Abbildung dargestellt. Eine falsch formatierte HTML-Zeichenfolge wird möglicherweise als Nur-Text angezeigt.

![HTML-Zeichenfolgenschnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichenfolgenschnellansicht")

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten Datenschnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Datenvisualisierungen](/visualstudio/mac/data-visualizations)