---
title: 'Fehler: Remotecomputer konnte die DCOM-Kommunikation nicht initiieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79548e2fbfbb4c10ce912ab90cd0541aea7f1200
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523357"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Fehler: Der Remotecomputer konnte die DCOM-Kommunikation nicht initiieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: Remotecomputer konnte die DCOM-Kommunikation nicht initiieren](https://docs.microsoft.com/visualstudio/debugger/error-remote-computer-could-not-initiate-dcom-communications).  
  
Bei einem Versuch des Remotecomputers, mit dem lokalen Computer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Der lokale Computer ist der Computer, auf dem  
  
 Visual Studio ausgeführt wird. Dieser Fehler kann mehrere Ursachen haben:  
  
-   Auf dem lokalen Computer ist eine Firewall aktiviert.  
  
-   Die Windows-Authentifizierung vom Remotecomputer zum lokalen Computer funktioniert nicht.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wenn auf dem lokalen Computer die Windows-Firewall aktiviert ist, finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Anleitungen zum Konfigurieren der Firewall für das lokale Debuggen.  
  
2.  Testen Sie die Windows-Authentifizierung, indem Sie versuchen, vom Remoteserver auf dem lokalen Computer eine Dateifreigabe zu öffnen.  
  
3.  Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)


