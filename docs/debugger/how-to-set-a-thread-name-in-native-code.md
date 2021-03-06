---
title: 'Vorgehensweise: Festlegen eines Threadnamens in nativem Code | Microsoft-Dokumentation'
ms.date: 12/17/2018
ms.topic: how-to
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ce6281a87900247cc54422a5175714d5f05b8e07
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349145"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Vorgehensweise: Festlegen eines Threadnamens in nativem Code
Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Die Benennung von Threads ist hilfreich, um beim Debuggen eines ausgeführten Prozesses relevante Threads im Fenster **Threads** zu identifizieren. Aussagekräftige Namen für Threads können auch nützlich sein, wenn Sie nachträgliches Debuggen über die Überprüfung von Absturzabbildern durchführen und Leistungserfassungen mithilfe verschiedener Tools analysieren.

## <a name="ways-to-set-a-thread-name"></a>Möglichkeiten zum Festlegen eines Threadnamens

Es gibt zwei Möglichkeiten, einen Threadnamen festzulegen. Bei der ersten Möglichkeit wird die Funktion [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) verwendet. Bei der zweiten wird eine bestimmte Ausnahme ausgelöst, während der Visual Studio-Debugger an den Prozess angefügt ist. Jeder Ansatz hat Vor- und Nachteile. Die Verwendung von `SetThreadDescription` wird ab Windows 10, Version 1607 oder Windows Server 2016 unterstützt.

Beachten Sie, dass _beide_ Ansätze bei Bedarf zusammen verwendet werden können, da ihre Mechanismen voneinander unabhängig sind.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Festlegen eines Threadnamens mithilfe von `SetThreadDescription`

Vorteile:
* Threadnamen sind beim Debuggen in Visual Studio unabhängig davon sichtbar, ob der Debugger zum Zeitpunkt des Aufrufs von „SetThreadDescription“ an den Prozess angefügt war.
* Threadnamen sind sichtbar, wenn Sie nachträgliches Debuggen durch Laden eines Absturzabbilds in Visual Studio ausführen.
* Threadnamen werden auch angezeigt, wenn Sie andere Tools verwenden, z. B. den [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools)-Debugger und die Leistungsanalyse [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).

Zu beachten:
* Threadnamen werden nur in Visual Studio 2017, Version 15.6 und höheren Versionen angezeigt.
* Wenn Sie nachträgliches Debuggen für eine Absturzabbilddatei ausführen, werden Threadnamen nur angezeigt, wenn der Absturz unter Windows 10, Version 1607, Windows Server 2016 oder neueren Windows-Versionen aufgetreten ist.

*Beispiel:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Festlegen eines Threadnamens durch Auslösen einer Ausnahme

Eine andere Möglichkeit zum Festlegen eines Threadnamens in Ihrem Programm besteht darin, dem Visual Studio-Debugger den gewünschten Threadnamen mitzuteilen, indem eine speziell konfigurierte Ausnahme ausgelöst wird.

Vorteile:
* Dies funktioniert in allen Visual Studio-Versionen.

Zu beachten:
* Dies funktioniert nur, wenn der Debugger zu dem Zeitpunkt angefügt ist, zu dem die ausnahmebasierte Methode verwendet wird.
* Threadnamen, die mit dieser Methode festgelegt werden, sind in Absturzabbildern oder Leistungsanalysetools nicht verfügbar.

*Beispiel:*

Mit der unten gezeigten `SetThreadName`-Funktion wird dieser ausnahmebasierte Ansatz veranschaulicht. Der Threadname wird automatisch in den Thread kopiert, damit der Arbeitsspeicher für den `threadName`-Parameter nach Abschluss des `SetThreadName`-Aufrufs freigegeben werden kann.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
- [How to: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)
