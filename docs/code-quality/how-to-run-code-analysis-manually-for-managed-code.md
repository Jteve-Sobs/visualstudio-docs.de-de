---
title: Manuelles Ausführen der Code Analyse für verwalteten Code
ms.date: 11/04/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 874d95b65b99af4b5a6b00d45101236f62db3df1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769370"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Gewusst wie: Manuelles Ausführen der Code Analyse für verwalteten Code (erfordert Visual Studio 2019, Version 16,5 oder höher)
Standardmäßig analysieren .NET Compiler Platform ("Roslyn")-Code Analysen ihren c#-oder Visual Basic Code bei der Typerstellung, indem Sie Live Analysen und während des Builds ausführen. Daher ist es normalerweise nicht erforderlich, die Code Analyse manuell zu initiieren. Es gibt jedoch einige Szenarien, in denen Sie ggf. die Code Analyse manuell auslassen möchten:

- Standardmäßig führt die Live Code Analyse Analysetools nur für geöffnete Dateien in Visual Studio aus. Möglicherweise interessieren Sie sich jedoch für die Anzeige von Code Analyse Warnungen für alle Dateien in einem bestimmten Projekt oder einer bestimmten Projekt Mappe. Wenn dies der Fall ist, empfiehlt es sich, die Code Analyse für ein Projekt oder eine Projekt Mappe einmal zu initiieren. Alternativ können Sie die kontinuierliche Live Code Analyse für die gesamte Projekt Mappe aktivieren. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren des Gültigkeits Bereichs der Live-Code Analyse für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md).
- Möglicherweise bevorzugen Sie den bedarfsgesteuerten Workflow für die Ausführung der Code Analyse für fortlaufende Live Analysen oder die Analyse der Buildzeit. Wenn dies der Fall ist, können Sie die Analyseprogramm Ausführung während der Live Analyse und/oder der Erstellung deaktivieren. Weitere Informationen zum Deaktivieren der Analyse finden [Sie unter Deaktivieren der Quell Code Analyse](disable-code-analysis.md). Anschließend sollten Sie die Code Analyse in einem Projekt oder einer Projekt Mappe einmal manuell Auslösers. 

### <a name="run-code-analysis-manually"></a>Manuelles Ausführen der Codeanalyse

1. Klicken Sie in **Projektmappen-Explorer**auf das Projekt.

2. Klicken Sie im Menü **analysieren** auf **Code Analyse für** *Projekt Name*ausführen.

Die Code Analyse wird im Hintergrund gestartet. In der Visual Studio-Statusleiste in der linken unteren Ecke wird die Meldung angezeigt, **dass die Code Analyse für \<project> ... ausgeführt** wird. Wenn die Code Analyse abgeschlossen ist, wird die Statusmeldung in die **Code Analyse \<project> abgeschlossen für **geändert. Die Fehlerliste wird in Kürze mit der gesamten Code Analyse Diagnose aktualisiert.
