---
title: Optionen, Text-Editor, C#, Erweitert
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ff42473c6f56d69a56cfbd811f2687ba544c7c5e
ms.sourcegitcommit: 4d932000a0f7e79c9475fe66c02fe9addcd7e47a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86181065"
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert

Mithilfe der Optionsseite **Erweitert** können Sie die Einstellungen für Formatierungen mithilfe des Editors, von Coderefactoring und XML-Dokumentationskommentaren für C# ändern. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Extras** > **Optionen** und anschließend auf **Text-Editor** > **C#**  > **Erweitert**.

> [!NOTE]
> Möglicherweise sind nicht alle Optionen hier aufgeführt.

## <a name="analysis"></a>Analyse

- Bereich für Livecodeanalyse oder Hintergrundanalyse

   Konfigurieren des Bereichs für die Hintergrundanalyse für verwalteten Code. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren des Bereichs für die Liveanalyse für verwalteten Code](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Using-Direktiven

- System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren

   Wenn er ausgewählt wurde, sortiert der Befehl **Remove and Sort Usings** (Using-Anweisungen entfernen und sortieren) im Kontextmenü die `using`-Anweisungen und platziert die „System“-Namespaces ganz oben in der Liste.

   Vor dem Sortieren:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Nach dem Sortieren:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Using-Direktivengruppen trennen

   Wenn ausgewählt, trennt der Befehl **Using-Anweisungen entfernen und sortieren** im Kontextmenü die `using`-Anweisungen, indem er eine leere Zeile zwischen Gruppen von Anweisungen einfügt, die den gleichen Stammnamespace aufweisen.

   Vor dem Sortieren:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Nach dem Sortieren:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

::: moniker range=">=vs-2019"                                              
- Using-Anweisungen für Typen in .NET Framework-Assemblys vorschlagen
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Using-Direktiven für Typen in Verweisassemblys vorschlagen
::: moniker-end                                                            

- Using-Direktiven für Typen in NuGet-Paketen vorschlagen

   Wenn diese Optionen ausgewählt wurden, ist eine [Schnellaktion](../quick-actions.md) zum Installieren eines NuGet-Pakets und Hinzufügen einer `using`-Anweisung für nicht referenzierte Typen verfügbar.

   ![Schnellaktion zum Installieren eines NuGet-Pakets in Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Markieren

- Verweise auf Symbole unter dem Cursor markieren

   Wenn sich der Cursor innerhalb eines Symbols befindet, oder wenn Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.

## <a name="outlining"></a>Gliedern

- Beim Öffnen von Dateien in Gliederungsmodus wechseln

   Wenn diese Option aktiviert ist, wird die Codedatei automatisch gegliedert. Hierdurch werden reduzierbare Codeblöcke erstellt. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.

- Zeilentrennzeichen zwischen Prozeduren anzeigen

   Der Text-Editor gibt den visuellen Bereich von Prozeduren an. In den *CS*-Quelldateien des Projekts werden an den in der folgenden Tabelle aufgeführten Positionen Linien gezeichnet:

   |Position in der CS-Quelldatei|Beispiel für die Linienposition|
   |---------------------------------|------------------------------|
   |Nach dem Schließen eines Blockdeklarationskonstrukts|– Am Ende einer Klasse, einer Struktur, eines Moduls, einer Schnittstelle oder einer Enumeration<br />– Hinter einer Eigenschaft, Funktion oder Sub<br />– Nicht zwischen den get- und set-Klauseln in einer Eigenschaft|
   |Nach mehreren Einzelzeilenkonstrukten|– Hinter Import-Anweisungen, vor einer Typdefinition in einer Klassendatei<br />– Hinter den in einer Klasse deklarierten Variablen, vor jeglichen Prozeduren|
   |Nach Einzelzeilendeklarationen (Deklarationen, die nicht auf Blockebene erfolgen)|– Nach Import-Anweisungen, Inherits-Anweisungen, Variablendeklarationen, Ereignisdeklarationen, Delegatdeklarationen und Declare-Anweisungen für DLLs|

## <a name="block-structure-guides"></a>Führungslinien für Blockstruktur

Aktivieren Sie diese Kontrollkästchen, um gestrichelte vertikale Linien zwischen geschweiften Klammern ( **{}** ) in Ihrem Code anzuzeigen. Dann können Sie leicht einzelne Codeblöcke für Ihre Deklarations- und Codeebenen erkennen.

## <a name="editor-help"></a>Editor-Hilfe

- XML-Dokumentationskommentare generieren für ///

   Bei Auswahl dieser Option werden die XML-Elemente für XML-Dokumentationskommentare eingefügt, wenn Sie die `///`-Kommentareinführung eingegeben haben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Siehe auch

- [How to: Einfügen von XML-Kommentaren für die Generierung der Dokumentation](../../ide/reference/generate-xml-documentation-comments.md)
- [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentieren von Code mit XML-Kommentaren (C#-Leitfaden)](/dotnet/csharp/codedoc)
- [Festlegen von sprachspezifischen Editoroptionen](../../ide/reference/setting-language-specific-editor-options.md)
- [C#-IntelliSense](../../ide/visual-csharp-intellisense.md)
