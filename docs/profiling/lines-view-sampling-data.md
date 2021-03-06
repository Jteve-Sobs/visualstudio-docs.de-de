---
title: Zeilenansicht - Samplingdaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff4d851937111400002de531696b9b69aec20ba9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778582"
---
# <a name="lines-view---sampling-data"></a>Zeilenansicht: Samplingdaten
In der Zeilenansicht der Samplingdaten werden die Leistungsdaten für die Anweisungen aufgeführt, die ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten. Eine Anweisung wird mit dem Folgenden identifiziert:

- Die Quelldatei, die die Funktionsanweisung enthält.

- Die Funktion, die die Anweisung enthält.

- Die Quellzeile, an der die Anweisung beginnt.

- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.

- Die Quellzeile, an der die Anweisung endet.

- Das Zeichen in der Quellzeile, an dem die Anweisung endet.

  Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.

  Per Definition ruft eine Anweisung keine anderen Funktionen auf. Daher sind nur exklusive Werte aufgeführt.

|Spalte|Beschreibung|
|------------|-----------------|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls, das die Funktionszeile enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktionszeile enthält.|
|**Quelldatei**|Die Quelldatei, die die Funktionszeile enthält.|
|**Funktionsname**|Der Name der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Funktionsadresse**|Die Startadresse der Funktion.|
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der dieses Sampling erfasst wurde.|
|**Quellendzeile**|Die Endzeilennummer der Quelldatei, an der dieses Sampling erfasst wurde.|
|**Quellanfangszeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem dieses Sampling erfasst wurde.|
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem dieses Sampling erfasst wurde.|
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile mit folgender Syntax:`Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number End` **,** `Character End` **]**|
|**Exklusive Samplings**|Die Anzahl von Samplings, die während der Ausführung der Funktionszeile gesammelt wurden.|
|**Exklusive Samplings %**|Der Prozentsatz aller Samplings bei der Profilerstellung, die gesammelt wurden, als die Funktionszeile ausgeführt wurde.|

## <a name="see-also"></a>Weitere Informationen
- [Zeilenansicht: Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)
