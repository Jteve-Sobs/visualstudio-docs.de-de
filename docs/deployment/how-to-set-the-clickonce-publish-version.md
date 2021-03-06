---
title: 'Gewusst wie: Festlegen der ClickOnce-Veröffentlichungs Version | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5e1d91de14e3da4f188c276ef7dd74943d8978
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382119"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion
Die- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Eigenschaft bestimmt, ob die Anwendung, die Sie veröffentlichen, als Update behandelt wird. Jedes Mal, wenn die Version erhöht wird, wird die Anwendung als Update veröffentlicht.

 Die- `Publish Version` Eigenschaft kann auf der Seite **veröffentlichen** des Projekt- **Designers**festgelegt werden.

> [!NOTE]
> Es gibt eine Projekt Option, mit der die `Publish Version` Eigenschaft bei jeder Veröffentlichung der Anwendung automatisch erhöht wird. diese Option ist standardmäßig aktiviert. Weitere Informationen finden Sie unter Gewusst [wie: Automatisches erhöhen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>So ändern Sie die Veröffentlichungs Version

1. Wenn ein Projekt in **Projektmappen-Explorer**ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Erhöhen Sie im Feld **Veröffentlichungs Version** die Versionsnummern **Major**, **Minor**, **Build**oder **Revision** .

    > [!NOTE]
    > Sie sollten nie eine Versionsnummer Dekrement. Dies kann zu unvorhersehbarem Update Verhalten führen.

## <a name="see-also"></a>Siehe auch
- [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)
- [Gewusst wie: Automatisches erhöhen der ClickOnce-Veröffentlichungs Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)