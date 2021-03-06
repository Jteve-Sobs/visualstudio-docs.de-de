---
title: 'Vorgehensweise: Angeben eines Startmenü namens für eine ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882d6f7471530a101404040368dbc6088e9b5d96
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381924"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Vorgehensweise: Angeben eines Namens im Startmenü für eine ClickOnce-Anwendung
Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung für die Online-und Offline Verwendung installiert wird, wird dem **Startmenü** und der Liste Software **Add or Remove Programs** ein Eintrag hinzugefügt. Standardmäßig ist der Anzeige Name mit dem Namen der Anwendungsassembly identisch, aber Sie können den anzeigen Amen ändern, indem Sie im Dialogfeld **Veröffentlichungs Optionen** den **Product Name** festlegen.

 Der **Produktname** wird auf der Seite " *publish.htm* " angezeigt. bei einer installierten offline Anwendung handelt es sich um den Namen des Eintrags im **Startmenü** . Außerdem handelt es **sich dabei um**den Namen, der in "Software" angezeigt wird.

 Der **Herausgeber Name** wird auf der *publish.htm* Seite oberhalb des **Produkt namens**angezeigt, und für eine installierte offline Anwendung ist dies auch der Name des Ordners, der das Anwendungssymbol im **Startmenü** enthält.

 Die Start Menü Verknüpfung oder die APP-Referenz wird in *%AppData%\Microsoft\Windows\Start menu\programme \\<Herausgeber Name \> *erstellt. Die Verknüpfung oder der APP-Verweis hat denselben Namen wie der Produktname.

 Sie können die Eigenschaften **Produktname** und **Herausgeber Name** im Dialogfeld **Veröffentlichungs Optionen** festlegen, das auf der Seite **veröffentlichen** des **Projekt-Designers**verfügbar ist.

### <a name="to-specify-a-start-menu-name"></a>So geben Sie einen Startmenü Namen an

1. Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.

2. Klicken Sie auf die Registerkarte **Veröffentlichen**.

3. Klicken Sie auf die Schaltfläche **Optionen** , um das Dialogfeld **Veröffentlichungs Optionen** zu öffnen.

4. Klicken Sie auf **Beschreibung**.

5. Geben Sie im Dialogfeld **Veröffentlichungs Optionen** den Namen ein, der unter **Produktname**angezeigt werden soll.

6. Optional können Sie einen Herausgeber Namen in den **Herausgeber Namen**eingeben.

## <a name="see-also"></a>Siehe auch
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [How to: Publish a ClickOnce application using the Publish Wizard (Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Veröffentlichungs-Assistenten)](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)