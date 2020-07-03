---
title: 'Fehler: Die Verbindung mit dem Computer &lt;Name&gt; konnte nicht hergestellt werden. Der Computer kann nicht im Netzwerk gefunden werden. | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8618a15ab4dcd6c9bbc0d9d8ab9bf347552883b1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460142"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Fehler: Die Verbindung mit dem Computer &lt;Name&gt; konnte nicht hergestellt werden. Der Computer kann nicht im Netzwerk gefunden werden.
Dieses Verhalten tritt auf, wenn eine der folgenden Bedingungen erfüllt ist:

- Die Verbindung zum Remotecomputer ist unterbrochen.

- Das Benutzerkonto auf dem Remotecomputer ist deaktiviert.

- Das Kennwort auf dem Remotecomputer ist abgelaufen.

### <a name="to-resolve-this-behavior"></a>So beheben Sie dieses Verhalten

- Stellen Sie sicher, dass der lokale Computer und der Remotecomputer im gleichen Netzwerk sind. Tun Sie dies, indem Sie mit dem Microsoft Windows Explorer (oder File Explorer) versuchen, auf den Remotecomputer zuzugreifen.

     – und –

- Stellen Sie sicher, dass das Benutzerkonto, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, aktiviert ist.

     – und –

- Stellen Sie sicher, dass das Kennwort, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, gültig und nicht abgelaufen ist.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)