---
title: 'Gewusst wie: Erstellen einer Zuordnung zwischen Entitäten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75d4fcc9b99c9c5e2960e152eb5dac1da1343109
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016936"
---
# <a name="how-to-create-an-association-between-entities"></a>Gewusst wie: Erstellen einer Zuordnung zwischen Entitäten
  Sie können Beziehungen zwischen Entitäten in Ihrem Business Data Connectivity (BDC)-Modell definieren, indem Sie Zuordnungen erstellen. Visual Studio generiert Methoden, die Consumer des Modells mit Informationen zu den einzelnen Zuordnungen bereitstellen. Diese Methoden können von SharePoint-Webparts, Listen oder benutzerdefinierten Anwendungen genutzt werden, um Daten Beziehungen in einer Benutzeroberfläche (UI) anzuzeigen.

 Sie können zwei Typen von Zuordnungen im BDC-Designer erstellen: Fremdschlüssel basierte Zuordnungen und Fremdschlüssel lose Zuordnungen. Weitere Informationen finden Sie unter [Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>So erstellen Sie eine Zuordnung zwischen Entitäten

1. Wählen Sie auf der Registerkarte **BusinessDataConnectivity** der **Toolbox**das **Zuordnungs Element aus** .

2. Wählen Sie im BDC-Designer die Quell Entität aus, und wählen Sie dann die Ziel Entität aus.

     Der Zuordnungs- **Editor** wird angezeigt.

3. Wenn Sie eine Fremdschlüssel basierte Zuordnung erstellen möchten, aktivieren Sie das Kontrollkästchen **ist Fremdschlüssel** Zuordnung.

    1. Wählen Sie in der Spalte **Quell-ID** der **bezeichnerzuordnungs** Tabelle den Bezeichner neben jedem passenden Typdeskriptor aus, der in der Spalte **Feld** angezeigt wird.

         Wählen Sie z. b **Source ID** . in der Spalte Quell `ContactID` -ID neben dem `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` Typdeskriptor und dem `ReadItem.salesOrder.SalesOrder.ContactID` Typdeskriptor aus.

4. Wenn Sie eine Fremdschlüssel Zuordnung erstellen möchten, deaktivieren Sie das Kontrollkästchen **ist Fremdschlüssel** Zuordnung.

5. Klicken Sie auf die Schaltfläche **OK** .

6. Im BDC-Designer wird eine Zeile, die die Zuordnung darstellt, zwischen der Quell Entität und der Ziel Entität angezeigt.

     Visual Studio fügt der Dienstklasse der Ziel Entität und der Dienstklasse der Quell Entität eine Association Navigator-Methode hinzu. Weitere Informationen zu Assoziations Navigationsmethoden finden Sie [unter Unterstützte Vorgänge](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. Fügen Sie in der Association Navigator-Methode der Source-Entität Code hinzu, der eine Auflistung von Ziel Entitäten zurückgibt.

8. Fügen Sie in der Association Navigator-Methode der Ziel Entität Code hinzu, der die zugehörige Quell Entität zurückgibt.

     Beispiele für Association Navigator-Methoden finden Sie unter [Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)
- [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
