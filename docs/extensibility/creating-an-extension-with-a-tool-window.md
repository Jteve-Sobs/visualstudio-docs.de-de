---
title: Erstellen einer Erweiterung mit einem Tool Fenster | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 597b84854dd398abee9dc21090e085273bc94c75
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903890"
---
# <a name="create-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Tool Fenster

In diesem Verfahren erfahren Sie, wie Sie mithilfe der VSIX-Projektvorlage und der Element Vorlage für **benutzerdefinierte Tool Fenster** eine Erweiterung mit einem Tool Fenster erstellen.

## <a name="prerequisites"></a>Voraussetzungen

 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Erstellen eines Tool Fensters

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **firstwindow**. Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine Tool Fenster-Element Vorlage mit dem Namen **MyWindow**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Add**  >  **Neues Element**hinzufügen aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **benutzerdefiniertes Tool Fenster**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Dateinamen des Tool Fensters in *MyWindow.cs*.

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

   Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

4. Wechseln Sie in der experimentellen Instanz zu **View**  >  **Weitere Fenster**anzeigen.

   Ein Menü Element für " **MyWindow**" sollte angezeigt werden. Klicken Sie auf diese Schaltfläche.

   Es sollte ein Tool Fenster mit dem Titel " **MyWindow** " und eine Schaltfläche mit dem Namen " **Click me!** " angezeigt werden.
