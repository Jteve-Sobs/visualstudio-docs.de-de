---
title: 'Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f057e2e4f9d39fd3c5d985b3f0d19751d508614
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769387"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers
Sie können Grafikinformationen über Ihren lokalen Computer oder einen Remotecomputer bzw. ein Remotegerät wiedergeben.

## <a name="choosing-a-playback-machine"></a>Auswählen eines Wiedergabecomputers
 Der Wiedergabecomputer ist ein Computer oder ein Gerät zur Wiedergabe von Grafikereignissen aus einem Grafikprotokoll. Normalerweise ist der lokale Computer die zweckmäßigste Option, jedoch kann ein Renderingproblem möglicherweise nicht auf einem Computer reproduziert werden, der über unterschiedliche Hardware- oder Treiberversionen als der Computer verfügt, der zur Aufzeichnung verwendet wurde. Ist dies der Fall, können Sie einen Remotewiedergabecomputer auswählen, der das Problem besser reproduziert, und trotzdem Ihren Entwicklungscomputer zur Diagnose verwenden.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>So verwenden Sie den lokalen Computer, um Grafikinformationen wiederzugeben

1. Klicken Sie im Dokumentfenster „Grafikprotokolle“ auf den Link **Wiedergabecomputer**. Das Dialogfeld **Verbindungen des Remotedebuggers** wird angezeigt.

2. Geben Sie unter **Manuelle Konfiguration** in der Eigenschaft **Adresse** `localhost` ein.

3. Setzen Sie die Eigenschaft **Authentifizierungsmodus** auf **Keine**.

4. Klicken Sie auf die Schaltfläche **Auswählen**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>So verwenden Sie einen Remotecomputer zur Wiedergabe von Grafikinformationen

1. Klicken Sie im Dokumentfenster „Grafikprotokolle“ auf den Link **Wiedergabecomputer**. Das Dialogfeld **Verbindungen des Remotedebuggers** wird angezeigt.

2. Geben Sie in der Eigenschaft **Adresse** unter **Manuelle Konfiguration** den Windows-Domänennamen oder die IP-Adresse des Computers oder Geräts ein, das Sie zur Wiedergabe von Grafikinformationen verwenden möchten.

3. Geben Sie die Art der Autorisierung an, die Sie verwenden möchten, um die Verbindung mit dem Wiedergabecomputer zu sichern.

    - Setzen Sie den **Authentifizierungsmodus** zur Windows-Authentifizierung auf **Windows**.

    - Wenn keine Authentifizierung erfolgen soll, legen Sie die Eigenschaft **Authentifizierungsmodus** auf **Keine** fest.

4. Klicken Sie auf die Schaltfläche **Auswählen**.

> [!NOTE]
> Im Dialogfeld **Verbindungen des Remotedebuggers** können auch Remotedebuggingziele angezeigt werden, die direkt mit Ihrem Entwicklungscomputer verbunden sind oder sich auf dem gleichen Subnetz befinden. Sie können eines dieser Remotedebuggingziele als Grafikdiagnose-Wiedergabecomputer verwenden, ohne diesen manuell zu konfigurieren. Wählen Sie im Dialogfeld **Verbindungen des Remotedebuggers** das gewünschte Ziel aus, und klicken Sie dann auf die Schaltfläche **Auswählen**.

## <a name="see-also"></a>Siehe auch
- [Grafikprotokolldokument](graphics-log-document.md)