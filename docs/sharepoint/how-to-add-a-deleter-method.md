---
title: 'Vorgehensweise: Hinzufügen einer Deleter-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd97d28936e9f0cc50e9064fdc1a6a64bb20fc77
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017044"
---
# <a name="how-to-add-a-deleter-method"></a>Gewusst wie: Hinzufügen einer Deleter-Methode
  Sie können Endbenutzern das Löschen eines Datensatzes aus einer externen Liste auf einer SharePoint-Website ermöglichen, indem Sie dem Modell eine Deleter-Methode hinzufügen. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>So erstellen Sie eine Deleter-Methode

1. Wählen Sie im **BDC-Designer**eine Entität aus.

2. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **BDC-Methoden Details**anzeigen aus.

    Das Fenster **BDC-Methoden Details** wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md).

3. Wählen Sie in der Liste **Methode hinzufügen** die Option **Deleter-Methode erstellen**aus.

    Visual Studio fügt dem Modell die folgenden Elemente hinzu. Diese Elemente werden im Fenster **Details der BDC-Methode** angezeigt.

   - Eine Methode mit dem Namen **Delete**.

   - Ein Eingabeparameter für die Methode.

   - Ein Typdeskriptor für den Parameter.

   - Eine Methoden Instanz für die Methode.

     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü der Dienst Code Datei, die für die Entität generiert wurde, und wählen Sie dann **Code anzeigen**aus.

    Die Entitäts Dienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zur Entitäts Dienst-Codedatei finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Fügen Sie der Deleter-Methode Code hinzu, um einen Datensatz zu löschen. Im folgenden Beispiel wird ein Zeilen Element aus einem Verkaufsauftrag mithilfe der AdventureWorks-Beispieldatenbank für SQL Server gelöscht.

   > [!NOTE]
   > Die-Methode in diesem Beispiel verwendet zwei Eingabeparameter.

   > [!NOTE]
   > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
