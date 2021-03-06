---
title: 'Vorgehensweise: Serialisieren von Symbolinformationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4ea056c48525014fffad0243dfeb4dd40a8daa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687013"
---
# <a name="how-to-serialize-symbol-information"></a>Vorgehensweise: Serialisieren von Symbolinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Symbole serialisieren, die zum Analysieren Ihrer Anwendung erforderlich sind. Die Serialisierung von Symbolen fügt Symbole in die VSP-Datei ein. Durch das Einfügen von Symbolinformationen in die VSP-Datei können andere Personen einen Leistungsbericht analysieren, ohne Zugriff auf die Originalsymbole zu haben. Wenn Symbole nicht serialisiert werden, müssen Sie die instrumentierte EXE- und PDB-Dateien zum Analysieren der VSP-Datei haben.  
  
### <a name="to-automatically-serialize-symbol-information"></a>So serialisieren Sie automatisch Symbolinformationen  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
2. Klicken Sie auf **Leistungstools**.  
  
3. Wählen Sie unter **Allgemeine Einstellungen** **Symbolinformationen automatisch serialisieren** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [Vorgehensweise: Analysierte Berichtsdateien speichern](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
