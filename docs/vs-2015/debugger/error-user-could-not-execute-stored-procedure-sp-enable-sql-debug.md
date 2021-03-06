---
title: 'Fehler: Benutzer konnte nicht führen Sie die gespeicherte Prozedur "sp_enable_sql_debug" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759386728283d3d39219133e53668afe3259714a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697675"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Fehler: Der Benutzer konnte die gespeicherte Prozedur „sp_enable_sql_debug“ nicht ausführen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die gespeicherte Prozedur "sp_enable_sql_debug" konnte auf dem Server nicht ausgeführt werden. Mögliche Ursachen:  
  
- Ein Verbindungsproblem. Es muss eine stabile Verbindung mit dem Server bestehen.  
  
- Fehlende erforderliche Berechtigungen für den Server. Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren-Rolle sein. Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows-Benutzerkonto (bei Windows-Authentifizierung) oder ein Konto mit Benutzer-ID und Kennwort (bei SQL-Authentifizierung).  
  
  Weitere Informationen finden Sie unter [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Legen Sie die SQL Server-Berechtigungen für das Debuggen](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Einrichten von SQL-Debugging](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
