---
title: Hinzufügen einer Schwellenwertregel für Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 9ee9f8c5ca052c101c5013f7fb2341efdc9cdfa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Vorgehensweise: Hinzufügen einer Schwellenwertregel mithilfe des Auslastungstest-Editors

In Auslastungstests werden mithilfe von Schwellenwertregeln Leistungsindikatorwerte entweder mit einem konstanten Wert oder mit einem anderen Leistungsindikatorwert verglichen.

## <a name="to-add-a-threshold-rule"></a>So fügen Sie eine Schwellenwertregel hinzu

1.  Öffnen Sie einen Auslastungstest.

2.  Erweitern Sie im Auslastungstest-Editor den Knoten **Indikatorensätze**.

3.  Erweitern Sie in einem der Indikatorensätze eine der **Indikatorenkategorien**. Sie können z.B. **LoadTest:Scenario** auswählen. Erweitern Sie den Knoten.

4.  Klicken Sie mit der rechten Maustaste auf einen der Indikatoren, z.B. **Benutzerauslastung** unter **LoadTest:Scenario**. Wählen Sie **Schwellenwertregel hinzufügen** aus.

     Das Dialogfeld **Schwellenwertregel hinzufügen** wird angezeigt.

5.  Sie können zwischen zwei Regeltypen wählen: Mit Konstante vergleichen oder Indikatoren vergleichen. Wählen Sie den gewünschten Typ, und legen Sie die Werte fest.

    > [!NOTE]
    > Legen Sie die **Warnung bei Überschreiten**-Eigenschaft auf **TRUE** fest, um anzugeben, dass das Überschreiten eines Schwellenwerts ein Problem darstellt, oder auf **FALSE** fest, um anzugeben, dass das Unterschreiten eines Schwellenwerts ein Problem darstellt.

## <a name="see-also"></a>Siehe auch

- [Analyzing Threshold Rule Violations (Analysieren von Verstößen gegen die Schwellenwertregel)](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)