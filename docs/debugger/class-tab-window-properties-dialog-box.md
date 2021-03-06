---
title: Registerkarte „Klasse“, Dialogfeld „Fenstereigenschaften“ | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565012"
---
# <a name="class-tab-window-properties-dialog-box"></a>Registerkarte "Klasse", Dialogfeld "Fenstereigenschaften"
Verwenden Sie die Registerkarte **Klasse**, um Informationen zur Klasse des ausgewählten Fensters anzuzeigen. Verschieben Sie den Fokus auf die [Fensteransicht](../debugger/windows-view.md), um das [Dialogfeld „Fenstereigenschaften“](../debugger/window-properties-dialog-box.md) anzuzeigen. Wählen Sie einen beliebigen Fensterknoten in der Struktur aus, und klicken Sie anschließend im Menü **Ansicht** auf **Eigenschaften**.

 Auf der Registerkarte **Klasse** sind folgende Einstellungen verfügbar:

|Eingabe|Beschreibung|
|-----------|-----------------|
|**Klassenname**|Der Name (oder die Ordnungszahl) dieser Fensterklasse|
|**Klassenstile**|Eine Kombination aus Klassenstilcodes|
|**Klassenbytes**|Anwendungsspezifische Daten, die dieser Fensterklasse zugeordnet sind|
|**Klassenatom**|Das vom **RegisterClass**-Aufruf zurückgegebene Atom für die Klasse|
|**Instanzhandle**|Diese Einstellung legt den Instanzhandle des Moduls fest, das die Klasse registriert hat. Instanzhandles sind nicht eindeutig.|
|**Fensterbytes**|Diese Einstellung legt die Anzahl zusätzlicher Bytes fest, die jedem Fenster dieser Klasse zugeordnet sind. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie das Listenfeld, um die Bytewerte im DWORD-Format anzuzeigen.|
|**Fensterprozedur**|Diese Einstellung legt die aktuelle Adresse der **WndProc**-Funktion für Fenster dieser Klasse fest. Diese unterscheidet sich von **Window Proc** (Fensterprozedur) auf der Registerkarte **Allgemein**, wenn das Fenster als Unterklasse definiert ist.|
|**Menüname**|Der Name des Hauptmenüs, das Fenstern dieser Klasse zugeordnet ist („none“ (keines), wenn kein Menü vorhanden ist)|
|**Symbolhandle**|Das Handle für das Symbol, das Fenstern dieser Klasse zugeordnet ist („none“ (keines), wenn kein Symbol vorhanden ist)|
|**Cursorhandle**|Das Handle für den Cursor, der Fenstern dieser Klasse zugeordnet ist („none“ (keiner), wenn kein Cursor vorhanden ist)|
|**Hintergrundpinsel**|Das Handle für den Hintergrundpinsel, der Fenstern dieser Klasse zugeordnet ist, oder eine der vordefinierten COLOR_*-Farben zum Zeichnen des Fensterhintergrunds („none“ (keiner), wenn kein Pinsel vorhanden ist)|