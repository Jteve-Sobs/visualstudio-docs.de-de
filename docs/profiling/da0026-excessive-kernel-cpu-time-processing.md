---
title: 'DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd3d96ccf3fc8463908ab5cf27b52e91fb1d05ef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544624"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung

|Element|Wert|
|-|-|
|Regel-ID|TODO|
|Kategorie|Verwendung der Profilerstellungstools|
|Profilerstellungsmethode|Sampling|
|Meldung|Ein relativ hohes Maß an CPU-Zeit für den Kernelmodus wurde festgestellt. Untersuchen Sie die Quelle bei aktiviertem SysCall-Sampling.|
|Regeltyp|Information|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="cause"></a>Ursache
 Die CPU-Zeit im Kernelmodus war größer als die Zeit im Benutzermodus. Wiederholen Sie die Profilerstellung, und führen Sie ein Sampling der Anzahl von Systemaufrufen (syscalls) aus, um die Ursache für die langen Ausführungszeiten im Kernelmodus zu ermitteln.

## <a name="rule-description"></a>Regelbeschreibung
 Die relativ lange Zeit, die sich die Anwendung im Kernelmodus befand, rechtfertigt möglicherweise eine nähere Untersuchung. Von einer Anwendung im Benutzermodus wird in den Kernelmodus gewechselt, sodass E/A-Vorgänge ausgeführt werden, auf Thread- oder Prozesssynchronisierungsprimitive gewartet wird oder Systemaufrufe ausgeführt werden. Sie können die Arten der von der Anwendung ausgeführten Systemaufrufe sowie die verantwortlichen Funktionen untersuchen, indem Sie die Option zum Sammeln von Beispielaufruflisten auf der Grundlage von Systemaufrufen aktivieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Führen Sie das Profil erneut aus, und wählen Sie die Option zum Sammeln von Samplings auf der Grundlage von Systemaufrufen aus, um die Arten der von der Anwendung ausgeführten Systemaufrufe zu untersuchen. Weitere Informationen finden Sie unter [How to: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md). Informationen zum Ausführen der Profilerstellungstools über die Befehlszeile finden Sie in der Befehlszeilentoolreferenz der Profilerstellungstools im Abschnitt **Samplingintervalloptionen** des Artikels [VSPerfCmd](../profiling/vsperfcmd.md).
