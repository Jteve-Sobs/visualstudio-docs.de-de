---
title: Referenz zu Abhängigkeits Diagrammen
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 774716dff6562b7792c6fa885c40db2a0a133136
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594564"
---
# <a name="dependency-diagrams-reference"></a>Abhängigkeits Diagramme: Referenz

In Visual Studio können Sie ein *Abhängigkeits Diagramm* verwenden, um die logische Architektur des Systems auf hoher Ebene visuell darzustellen. Ein Abhängigkeits Diagramm organisiert die physischen Artefakte in Ihrem System in logische, abstrakte Gruppen, die als *Ebenen*bezeichnet werden. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.

Welche Editionen von Visual Studio diese Funktion unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Abhängigkeits Diagramme für .net Core-Projekte werden ab Visual Studio 2019 Version 16,2 unterstützt.

Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Wenn Sie Ihr System in Ebenen organisieren, die unterschiedliche Rollen und Funktionen beschreiben, kann ein Abhängigkeits Diagramm Ihnen helfen, den Code besser zu verstehen, wiederzuverwenden und zu pflegen.

Verwenden Sie ein Abhängigkeits Diagramm, um die folgenden Aufgaben auszuführen:

- Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems

- Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur

- Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems

- Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge

In diesem Thema werden die Elemente beschrieben, die Sie in einem Abhängigkeits Diagramm verwenden können. Ausführlichere Informationen zum Erstellen und Zeichnen von Abhängigkeits Diagrammen finden Sie unter [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md). Weitere Informationen zu ebenenmustern finden Sie auf der [Seite Patterns & Practices](https://archive.codeplex.com/?p=apparch).

## <a name="reading-dependency-diagrams"></a>Lesen von Abhängigkeits Diagrammen

![Elemente in Abhängigkeits Diagrammen](../modeling/media/uml_layerrefreading.png)

In der folgenden Tabelle werden die Elemente beschrieben, die Sie in einem Abhängigkeits Diagramm verwenden können.

|**Gebildet**|**Element**|**Beschreibung**|
|-|-|-|
|1|**Deck**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> Um die mit einer Ebene verknüpften Artefakte anzuzeigen, öffnen Sie das Kontextmenü für die Ebene, und klicken Sie dann auf **Links anzeigen** , um den **Ebenen-Explorer**zu öffnen.<br /><br /> Weitere Informationen finden Sie unter [Ebenen-Explorer](#Explorer).<br /><br /> -   unzulässige **Namespace Abhängigkeiten** : gibt an, dass die dieser Ebene zugeordneten Artefakte nicht von den angegebenen Namespaces abhängen können.<br />-   unzulässige **Namespaces** : gibt an, dass die dieser Ebene zugeordneten Artefakte nicht zu den angegebenen Namespaces gehören dürfen.<br />-   **erforderliche Namespaces** : gibt an, dass die dieser Ebene zugeordneten Artefakte zu einem der angegebenen Namespaces gehören müssen.|
|2|**Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Richtung** : gibt die Richtung der Abhängigkeit an.|
|3|**Bidirektionale Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Richtung** : gibt die Richtung der Abhängigkeit an.|
|4|**Kommentar**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|
|5|**Kommentar Verknüpfung**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|

## <a name="Explorer"></a>Ebenenexplorer

Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:

- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

     Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:

- [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Überprüfen der verknüpften Artefakte

Öffnen Sie im Abhängigkeits Diagramm das Kontextmenü für eine oder mehrere Ebenen, und wählen Sie dann **Verknüpfungen anzeigen**aus.

Der **Ebenen-Explorer** wird geöffnet und zeigt die Artefakte an, die mit den ausgewählten Ebenen verknüpft sind. Der **ebenenexplorer** verfügt über eine Spalte, in der die einzelnen Eigenschaften der artefaktlinks angezeigt werden.

> [!NOTE]
> Wenn nicht alle diese Eigenschaften angezeigt werden, erweitern Sie das Fenster **Ebenen-Explorer** .

|**Spalte im ebenenexplorer**|**Beschreibung**|
|-|-|
|**Kategorien**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|
|**Deck**|Die Ebene, die mit dem Artefakt verknüpft ist.|
|**Unterstützt Validierung**|Wenn **true**, kann der ebenenvalidierungsprozess überprüfen, ob das Projekt Abhängigkeiten zu oder von diesem Element entspricht.<br /><br /> Wenn der Wert **false**ist, wird der Link nicht an dem ebenenvalidierungsprozess beteiligt.<br /><br /> Weitere Informationen finden Sie unter [Abhängigkeits Diagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).|
|**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|

## <a name="see-also"></a>Siehe auch

- [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
