---
title: Debuggen von Komponententests mit dem Test-Explorer
description: Hier erfahren Sie, wie Sie mit dem Test-Explorer in Visual Studio Komponententests debuggen.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2def56c6a3860ce0476f448f87bdde25c7970807
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86393539"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Debuggen und Analysieren von Komponententests mit dem Test-Explorer

Mit dem Test-Explorer können Sie Debugsitzungen für Tests starten. Beim schrittweisen Durchlaufen des Codes mit dem Visual Studio-Debugger wechseln Sie nahtlos zwischen den Komponententests und dem zu testenden Projekt hin und zurück. Starten des Debuggens:

1. Legen Sie im Visual Studio-Editor in mindestens einer zu debuggenden Testmethode einen Haltepunkt fest.

    > [!NOTE]
    > Da Testmethoden in jeder die oft ausgegebene Befehlszeilen  Reihenfolge ausgeführt werden können, legen Sie Haltepunkte in allen Testmethoden fest, die Sie debuggen möchten.

::: moniker range="vs-2017"
2. Wählen Sie im Test-Explorer die Testmethode(n) aus, und klicken Sie dann im Kontextmenü auf **Ausgewählte Tests debuggen**.
::: moniker-end
::: moniker range=">=vs-2019"
2. Wählen Sie im Test-Explorer die Testmethode(n) aus, und klicken Sie dann im Kontextmenü auf **Debuggen**.

   ![Details zur Testausführung](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Weitere Informationen zum Debugger finden Sie unter [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnose von Leistungsproblemen bei Testmethoden

::: moniker range="vs-2017"
Zur Ermittlung der Ursache, weshalb die Ausführung einer Testmethode zu lange dauert, müssen Sie im Test-Explorer die Methode auswählen und anschließend im Kontextmenü auf **Profil für ausgewählten Test erstellen** klicken. Weitere Informationen finden Sie unter [Grundlagen zu Instrumentierungsdatenwerten](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

::: moniker range=">=vs-2019"
Zur Ermittlung der Ursache, weshalb die Ausführung einer Testmethode zu lange dauert, müssen Sie im Test-Explorer die Methode auswählen und anschließend im Kontextmenü auf **Profil** klicken. Weitere Informationen finden Sie unter [Grundlagen zu Instrumentierungsdatenwerten](../profiling/understanding-instrumentation-data-values.md?view=vs-2017).
::: moniker-end

> [!NOTE]
> Dieses Feature wird für .NET Core derzeit nicht unterstützt.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)
- [Häufig gestellte Fragen zum Test-Explorer](test-explorer-faq.md)
