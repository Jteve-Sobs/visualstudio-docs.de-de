---
title: Bilder und Symbole für Visual Studio | Microsoft-Dokumentation
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbf1542277189f37565e7ff415a52025094e595
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85906117"
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Verwendung von Images in Visual Studio
 Vor dem Erstellen von Grafiken sollten Sie die 1000 Bilder in der [Visual Studio-Bildbibliothek](https://www.microsoft.com/download/details.aspx?id=35825)verwenden.

### <a name="types-of-images"></a>Abbild Typen

- **Symbole**. Kleine Bilder, die in Befehlen, Hierarchien, Vorlagen usw. angezeigt werden. Die in Visual Studio verwendete Standard Symbolgröße ist 16x16 PNG. Symbole, die vom Image Dienst erzeugt werden, generieren automatisch das XAML-Format für die hdpi-Unterstützung.

    > [!NOTE]
    > Während Bilder im Menüsystem verwendet werden, sollten Sie kein Symbol für jeden Befehl erstellen. Sehen Sie sich die [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) an, um zu sehen, ob Ihr Befehl ein Symbol abrufen soll.

- **Thumbnails.** Bilder, die im Vorschaubereich eines Dialog Felds verwendet werden, z. b. das Dialogfeld "Neues Projekt".

- **Dialog Bilder.** Bilder, die in Dialogfeldern oder Assistenten angezeigt werden, entweder als beschreibende Grafiken oder Nachrichten Indikatoren. Verwenden Sie nur selten und nur, wenn dies notwendig ist, um ein schwieriges Konzept zu veranschaulichen oder die Aufmerksamkeit des Benutzers zu erhalten (Warnung, Warnung).

- **Animierte Bilder.** Wird in Fortschrittsindikatoren, Status leisten und Vorgangs Dialogfeldern verwendet.

- **Cursor.** Wird verwendet, um anzugeben, ob ein Vorgang mit der Maus zulässig ist, wo ein Objekt gelöscht werden kann, usw.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Symbol Entwurf

### <a name="overview"></a>Übersicht
 Visual Studio verwendet Symbole im modernen Stil, die eine saubere Geometrie und einen 50/50-Saldo von positiv/negativ (hell/dunkel) aufweisen und direkte, verständliche Metaphern verwenden. Wichtige Symbol Entwurfs Punkte zentrieren Klarheit, Vereinfachung und Kontext.

- **Klarheit:** konzentrieren Sie sich auf die Kern Metapher, die die Bedeutung und die Individualität eines Symbols liefert.

- **Vereinfachung:** reduzieren Sie das Symbol auf seine kernbedeutung, und bringen Sie das Design nur mit den erforderlichen Elementen und ohne Frills in das Design.

- **Kontext:** berücksichtigen Sie bei der Konzeptentwicklung alle Aspekte der Rolle eines Symbols. Dies ist entscheidend, wenn Sie entscheiden, welche Elemente die Kern Metapher des Symbols bilden.

  Bei Symbolen gibt es eine Reihe von Entwurfs Punkten, die vermieden werden sollten:

- Verwenden Sie nur dann Symbole, die Benutzeroberflächen Elemente darstellen. Wählen Sie einen abstrakten oder symbolischen Ansatz aus, wenn das UI-Element weder allgemein noch offensichtlich oder eindeutig ist.

- Verwenden Sie keine allgemeinen Elemente, wie z. b. Dokumente, Ordner, Pfeile und die Lupe. Verwenden Sie diese Elemente nur, wenn dies für die Bedeutung des Symbols von Bedeutung ist. Beispielsweise sollte die nach rechts ausgerichtete Lupe nur die Such-, Such-und Suchvorgänge angeben.

- Obwohl einige Legacy Symbol Elemente die Verwendung von Perspektiven beibehalten, erstellen Sie keine neuen Symbole mit Perspektiven, es sei denn, das Element weist keine Klarheit auf.

- Nicht zu viele Informationen in einem Symbol. Ein einfaches Bild, das leicht erkannt oder als erkennbares Symbol erlernt werden kann, ist viel nützlicher als ein übermäßig komplexes Bild. Ein Symbol kann die ganze Story nicht teilen.

### <a name="icon-creation"></a>Symbol Erstellung

#### <a name="concept-development"></a>Konzeptentwicklung
 Visual Studio verfügt in seiner Benutzeroberfläche über eine Vielzahl von Symboltypen. Berücksichtigen Sie bei der Entwicklung sorgfältig den Symboltyp. Verwenden Sie für Ihre Symbol Elemente keine unklaren oder ungewöhnlichen UI-Objekte. Wählen Sie in diesen Fällen symbolisch aus, z. b. mit dem Smarttag-Symbol. Beachten Sie, dass die Bedeutung des abstrakten Tags auf der linken Seite offensichtlicher ist als die vage, auf der Benutzeroberfläche basierende Version auf der rechten Seite:

|**Korrekte Verwendung von symbolischen Bildern**|**Falsche Verwendung von symbolischen Bildern**|
|-|-|
|![Symbol für richtiges Smarttag](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Es gibt Instanzen, in denen standardmäßig leicht erkennbare Benutzeroberflächen Elemente für Symbole gut funktionieren. Das Fenster hinzufügen ist ein Beispiel:

|**Korrigieren des Benutzeroberflächen Elements in einem Symbol**|**Falsches UI-Element in einem Symbol**|
|-|-|
|![Richtiges Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsches Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Verwenden Sie kein Dokument als Basiselement, es sei denn, es ist für die Bedeutung des Symbols von Bedeutung. Ohne das Document-Element in Add Document (unten) geht die Bedeutung verloren, während bei der Aktualisierung das Dokument Element für die Kommunikation mit der Bedeutung unnötig ist.

|**Korrekte Verwendung des Dokument Symbols**|**Falsche Verwendung des Dokument Symbols.**|
|-|-|
|![Richtiges Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Das Konzept von "Show" sollte durch das Symbol dargestellt werden, das am besten veranschaulicht, was angezeigt wird, z. b. mit dem Beispiel "alle Dateien anzeigen". Wenn erforderlich, z. b. mit dem Ressourcenansicht Beispiel, kann die Darstellung eines "View"-Konzepts verwendet werden.

|**Auftritt**|**Anschauung**|
|-|-|
|![Symbol "Anzeigen"](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Symbol "Ansicht"](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Das rechts gerichtete Lupensymbol sollte nur Suche, suchen und Durchsuchen darstellen. Der links gerichtete Variant mit dem Pluszeichen oder Minuszeichen sollte nur Zoom-und Zoom Zeichen darstellen.

|**Such**|**Skala**|
|-|-|
|![Suchsymbol](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Verwenden Sie in Struktur Ansichten nicht sowohl das Ordnersymbol als auch einen Modifizierer. Wenn verfügbar, verwenden Sie nur den-Modifizierer.

|**Richtige Strukturansicht-Symbole**|**Falsche Strukturansicht-Symbole**|
|-|-|
|![Richtiges Strukturansicht-Symbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![richtiges Struktur Ansichts Symbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches Strukturansicht-Symbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![falsches Struktur Ansichts Symbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Details zum Stil

#### <a name="layout"></a>Layout
 Stapel Elemente, wie für die Standard-16x16-Symbole angezeigt:

 ![Layoutstack für 16x16-Symbole](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Layoutstack für 16x16-Symbole

 Status Benachrichtigungs Elemente werden besser als eigenständige Symbole verwendet. Es gibt jedoch Kontexte, in denen eine Benachrichtigung auf das Basiselement gestapelt werden soll, z. b. mit dem Symbol "Aufgabe vervollständigen":

 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Eigenständige Benachrichtigungs Symbole

 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Symbol "Aufgabe vervollständigen"

 Projekt Symbole sind in der Regel ICO-Dateien, die mehrere Größen enthalten. Die meisten 16x16-Symbole enthalten dieselben Elemente. Die 32 x 32-Versionen haben weitere Details, einschließlich des Projekt Typs, sofern zutreffend.

 ![Projektsymbole in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Projekt Symbole für VB-Windows-Steuerelement Bibliothek, 16x16 und 32x32

 Zentrieren Sie ein Symbol innerhalb seines Pixel Rahmens. Wenn dies nicht möglich ist, richten Sie das Symbol am oberen und/oder rechten Rand des Frames aus.

 ![Innerhalb des Pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Innerhalb des Pixelframes zentriertes Symbol

 ![Am Pixelframe oben rechts ausgerichtetes Symbol](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Symbol, das am oberen rechten Rand des Frames ausgerichtet ist

 ![Am Pixelframe oben rechts ausgerichtetes und zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Symbol zentriert und am oberen Rand des Frames ausgerichtet

 Um optimale Ausrichtung und Ausgewogenheit zu erzielen, sollten Sie das Basiselement des Symbols nicht durch Aktions Symbole behindern. Platzieren Sie das Symbol in der Nähe der oberen linken Ecke des Basis Elements. Wenn Sie ein zusätzliches Element hinzufügen, sollten Sie die Ausrichtung und den Saldo des Symbols in Erwägung gezogen.

|**Richtige Ausrichtung und Ausgewogenheit**|**Falsche Ausrichtung und Ausgewogenheit**|
|-|-|
|![Richtige Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Stellen Sie die Größen Parität für Symbole sicher, die Elemente gemeinsam verwenden und in Sätzen verwendet werden. Beachten Sie, dass der Kreis und der Pfeil bei falscher Kopplung überdimensioniert sind und nicht stimmen.

|**Richtige Größen Parität**|**Falsche Größen Parität**|
|-|-|
|![Richtige Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Verwenden Sie konsistente Linien-und visuelle Gewichtungen. Überprüfen Sie, wie das Symbol, das Sie aufbauen, mithilfe eines parallelen Vergleichs mit anderen Symbolen verglichen wird. Verwenden Sie niemals den gesamten 16x16-Frame, und verwenden Sie 15 x 15 oder kleiner. Das Minus-zu-positiv-Verhältnis (dunkel-zu-hell) sollte 50/50 sein.

|**Verhältnis von negativ zu positiv**|**Falsches minus-zu-positiv-Verhältnis**|
|-|-|
|![Richtige visuelle Gewichtung für Symbole &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Richtige visuelle Gewichtung für Symbole &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Richtige visuelle Gewichtung für Symbole &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Verwenden Sie einfache, vergleichbare Formen und ergänzende Winkel, um ihre Elemente zu erstellen, ohne die Integrität der Elemente zu beeinträchtigen. Verwenden Sie nach Möglichkeit 45 °-oder 90 °-Winkel.

 ![Richtige Symbolwinkel](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektive
 Lassen Sie das Symbol klar und verständlich. Verwenden Sie die Perspektive und eine Lichtquelle nur, wenn dies erforderlich ist. Obwohl die Verwendung von Perspective für Symbol Elemente vermieden werden sollte, sind einige Elemente ohne Sie nicht erkennbar. In solchen Fällen kommuniziert eine stilisierte Perspektive mit der Klarheit des Elements.

 ![3-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3-Punkt-Perspektive

 ![1-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1-Punkt-Perspektive

 Die meisten Elemente sollten nach rechts ausgerichtet oder abgekoppelt werden:

 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Verwenden Sie Lichtquellen nur dann, wenn Sie einem Objekt die erforderliche Klarheit hinzufügen.

|**Richtige Lichtquelle**|**Falsche Lichtquelle.**|
|-|-|
|![Richtige Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Verwenden Sie Kontur, um die Lesbarkeit zu verbessern oder die Metapher besser zu kommunizieren. Das minus-positiv-Guthaben (dunkel hell) sollte 50/50 sein.

|**Korrekte Verwendung von umrissen**|**Falsche Verwendung von umrissen**|
|-|-|
|![Richtige Konturen](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Symboltypen
 **Shell-und Befehls** leisten Symbole bestehen aus höchstens drei der folgenden Elemente: eine Basis, ein Modifizierer, eine Aktion oder ein Status.

 ![Beispiele für Shell-und Befehls leisten Symbole](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Beispiele für Shell-und Befehls leisten Symbole

 Symbole der **Tool Fenster-Befehlsleiste** bestehen aus maximal drei der folgenden Elemente: eine Basis, ein Modifizierer, eine Aktion oder ein Status.

 ![Beispiele für Tool Fenster-Befehls leisten Symbole](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Beispiele für Tool Fenster-Befehls leisten Symbole

 Struktur **Ansicht-Disambiguator** -Symbole bestehen aus höchstens drei der folgenden Elemente: eine Basis, ein Modifizierer, eine Aktion oder ein Status.

 ![Beispiele für Strukturansicht-Disambiguator-Symbole](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Beispiele für Strukturansicht-Disambiguator-Symbole

 Die Symbole der **Zustands basierten Wert Taxonomie** sind in den folgenden Zuständen vorhanden: "aktiv", "aktiv deaktiviert" und "inaktiv" deaktiviert.

 ![Beispiele für die Symbole der Zustands basierten Wert Taxonomie](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Beispiele für die Symbole der Zustands basierten Wert Taxonomie

 **IntelliSense** -Symbole bestehen aus höchstens drei der folgenden Elemente: eine Basis, ein Modifizierer und ein Status.

 ![Beispiele für IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Beispiele für IntelliSense-Symbole

 **Kleine (16x16) Projekt** Symbole dürfen nicht mehr als zwei Elemente enthalten: einen Basis-und einen Modifizierer.

 ![Beispiele für kleine (16x16) Projekt Symbole](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 Project Icon &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 Project Icon &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Beispiele für kleine (16x16) Projekt Symbole

 **Große (32x32) Projekt** Symbole bestehen aus höchstens vier der folgenden Elemente: eine Basis, ein bis zwei Modifizierer und eine sprach Überlagerung.

 ![Beispiele für große (32x32) Projekt Symbole](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Beispiele für große (32x32) Projekt Symbole

### <a name="production-details"></a>Produktionsdetails
 Alle neuen Benutzeroberflächen Elemente sollten mit Windows Presentation Foundation (WPF) erstellt werden, und alle neuen Symbole für WPF sollten das 32-Bit-PNG-Format aufweisen. Das 24-Bit-PNG ist ein Legacy Format, das keine Transparenz unterstützt und daher nicht für Symbole empfohlen wird.

 Speichern Sie die Auflösung bei 96 dpi.

#### <a name="file-types"></a>Dateitypen

- **32-Bit PNG:** das bevorzugte Format für Symbole. Ein verlustfreies Daten Komprimierungs Dateiformat, mit dem ein einzelnes Rasterbild (Pixel) gespeichert werden kann. 32-Bit-PNG-Dateien unterstützen Alphakanal Transparenz, Gammakorrektur und Interlacing.

- **32-Bit-BMP:** für nicht-WPF-Steuerelemente. 32-Bit-BMP wird auch als XP oder High Color bezeichnet und ist ein RGB/a-Bildformat, ein wahr farbiges Bild mit einer Alphakanal Transparenz. Der Alphakanal ist eine in Adobe Photoshop festgelegte Ebene der Transparenz, die dann in der Bitmap als zusätzlicher (vierter) Farbkanal gespeichert wird. Ein schwarzer Hintergrund wird bei der Produktion von Grafiken zu allen 32-Bit-BMP-Dateien hinzugefügt, um einen schnellen visuellen Hinweis auf die Farbtiefe zu bieten. Dieser schwarze Hintergrund stellt den Bereich dar, der in der Benutzeroberfläche maskiert werden soll.

- **32-Bit-ICO:** für Projekt Symbole und Element hinzufügen. Alle ICO-Dateien sind eine 32-Bit-True-Farbe mit Alphakanal Transparenz (RGB/A). Da ICO-Dateien mehrere Größen und Farbtiefe speichern können, liegen Vista-Symbole häufig in einem ICO-Format vor, das die Bildgrößen 16x16, 32x32, 48x48 und 256x256 enthält. Um in Windows-Explorer ordnungsgemäß angezeigt zu werden, müssen ICO-Dateien für jede Bildgröße in 24-Bit-und 8-Bit-Farbtiefe gespeichert werden.

- **XAML:** für Entwurfs Oberflächen und Windows-Adorner. XAML-Symbole sind vektorbasierte Bilddateien, die Skalierung, Rotation, Einreichung und Transparenz unterstützen. Sie sind heute nicht in Visual Studio üblich, werden aber aufgrund ihrer Flexibilität immer beliebter.

- **SVG**

- **24-Bit-BMP:** für die Visual Studio-Befehlsleiste. Ein Format des Formats "True-Color RGB" (24-Bit-BMP) ist eine Symbol Konvention, die eine Ebene der Transparenz mithilfe von Magenta (R = 255, G = 0, B = 255) als Farbschlüssel für eine Abbild Transparenz Ebene erstellt. In einem 24-Bit-BMP werden alle Magenta-Oberflächen unter Verwendung der Hintergrundfarbe angezeigt.

- **24-Bit-GIF:** für die Visual Studio-Befehlsleiste. Ein Format für die echt farbige RGB-Grafik, das Transparenz unterstützt. GIF-Dateien werden häufig in Assistenten-Grafiken und GIF-Animationen verwendet.

### <a name="icon-construction"></a>Symbol Erstellung
 Die kleinste Symbolgröße in Visual Studio ist 16x16. Die größte häufige Verwendung ist 32x32. Beachten Sie, dass der gesamte 16x16-, 24x24-oder 32x32-Frame nicht aufgefüllt wird, wenn ein Symbol entworfen wird. Eine lesbare, einheitliche Symbol Erstellung ist für die Benutzer Erkennung von entscheidender Bedeutung. Beachten Sie bei der Erstellung von Symbolen die folgenden Punkte.

- Symbole sollten klar, verständlich und konsistent sein.

- Es ist besser, die Status Benachrichtigungs Elemente als einzelne Symbole zu verwenden und Sie nicht oberhalb eines Symbol Basis Elements zu stapeln. In bestimmten Kontexten erfordert die Benutzeroberfläche möglicherweise, dass das Status-Element mit einem Basiselement gekoppelt ist.

- Projekt Symbole sind in der Regel ICO-Dateien, die mehrere Größen enthalten. Nur die Symbole 16x16, 24x24 und 32x32 werden aktualisiert. Die meisten 16x16-und 24x24-Symbole enthalten dieselben Elemente. Die Symbole 32x32 enthalten weitere Details, einschließlich des Projekt sprach Typs, sofern zutreffend.

- Für 32 x 32-Symbole verfügen die Basiselemente in der Regel über eine Linien Gewichtung von 2 Pixeln. Für Detail Elemente kann eine Zeilen Gewichtung von 1 oder 2 Pixel verwendet werden. Verwenden Sie das beste Urteil, um zu bestimmen, welche besser geeignet ist.

- Es muss mindestens ein 1-Pixel-Abstand zwischen Elementen für die Symbole 16x16 und 24x24 vorhanden sein. Verwenden Sie für 32-x-32-Symbole 2 Pixel Abstand zwischen Elementen und zwischen dem-Modifizierer und dem Basiselement.

  ![Element Abstand für die Symbole mit der Größenanpassung 16x16, 24x24 und 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Element Abstand für die Symbole mit der Größenanpassung 16x16, 24x24 und 32x32

#### <a name="color-and-accessibility"></a>Farbe und Barrierefreiheit
 Visual Studio-Kompatibilitätsrichtlinien erfordern, dass alle Symbole im Produkt die Barrierefreiheits Anforderungen für Farbe und Kontrast bestehen. Dies wird durch Symbol Inversion erreicht. Wenn Sie entwerfen, sollten Sie sich bewusst sein, dass Sie im Produktprogramm gesteuert invertiert werden.

 Weitere Informationen zur Verwendung von Farben in Visual Studio-Symbolen finden Sie unter [Verwenden von Farbe in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Verwenden von Farbe in Bildern

### <a name="overview"></a>Übersicht
 Symbole in Visual Studio sind hauptsächlich Monochromatisch. Die Farbe ist für das vermitteln spezifischer Informationen und nie für die Dekoration reserviert. Farbe wird verwendet:

- So geben Sie eine Aktion an

- so Benachrichtigen Sie den Benutzer über eine Status Benachrichtigung

- So bestimmen Sie die sprach Zugehörigkeit

- So unterscheiden Sie Elemente in IntelliSense

### <a name="accessibility"></a>Zugriff
 Visual Studio-Kompatibilitätsrichtlinien erfordern, dass alle in das Produkt eingecheckten Symbole die Barrierefreiheits Anforderungen für Farbe und Kontrast erfüllen. Farben in der Palette der visuellen Sprache wurden getestet und erfüllen diese Anforderungen.

#### <a name="color-inversion-for-dark-themes"></a>Farb Inversion für dunkles Design
 Um Symbole mit dem richtigen Kontrastverhältnis im Visual Studio-Design "dunkel" anzuzeigen, wird eine Inversion Programm gesteuert angewendet. Die Farben in diesem Handbuch wurden teilweise ausgewählt, damit Sie ordnungsgemäß umkehren. Schränken Sie die Verwendung von Farben auf diese Palette ein, oder Sie erhalten unvorhersehbare Ergebnisse, wenn die Inversion angewendet wird.

 ![Beispiele für Symbole, deren Farben umgekehrt waren](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Beispiele für Symbole, deren Farben umgekehrt waren

### <a name="base-palette"></a>Basis Palette
 Alle Standardsymbole enthalten drei Basis Farben. Symbole enthalten keine Farbverläufe oder Schlag Schatten, mit einer oder zwei Ausnahmen für 3D-Tool Symbole.

|Verbrauch|name|Value (helles Design)|Swatch|Beispiel|
|-----------|----------|---------------------------|------------|-------------|
|Hintergrund/dunkel|VS BG|424242/66, 66, 66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Beispiel für Basispalette](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Vordergrund/Licht|VS FG|F0EFF1/240.239.241|![Muster F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Kontur|VS out|F6F6F6/246.246.246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Zusätzlich zu den Basis Farben kann jedes Symbol eine zusätzliche Farbe aus der erweiterten Palette enthalten.

### <a name="extended-palette"></a>Erweiterte Palette

#### <a name="action-modifiers"></a>Aktionsmodifizierer
 Die vier folgenden Farben geben die Typen von Aktionen an, die von Aktionsmodifizierer benötigt werden:

|Verbrauch|name|Wert (alle Designs)|Swatch|
|-----------|----------|--------------------------|------------|
|Positiv|VS-Aktion grün|388a34/56138, 52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativ|VS-Aktion rot|A1260D/161, 38, 13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS-Aktion blau|00539c/0, 83156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Erstellen/neu|VS-Aktion Orange|C27D1A/194156, 26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Beispiele
 Grün wird für positive Aktionsmodifizierer wie "Add", "Run", "Play" und "Validate" verwendet.

|Ausführen|Abfrage ausführen|Alle Schritte wiedergeben|Steuerelement hinzufügen|
|-|-|-|-|
|![Symbol "Ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Symbol "Abfrage ausführen"](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Symbol "Alle Schritte wiedergeben"](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Symbol "Steuerelement hinzufügen"](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Rot wird für negative Aktionsmodifizierer wie "Delete", "beenden", "Abbrechen" und "Schließen" verwendet.

|Löschen der Beziehung|Spalte löschen|Abfrage abbrechen|Verbindung offline|
|-|-|-|-|
|![Symbol "Beziehung löschen"](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Symbole "Spalte löschen"](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Symbol "Abfrage beenden"](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Blue wird auf neutrale Aktionsmodifizierer angewendet, die am häufigsten als Pfeile dargestellt werden, z. b. "Open", "Next", "Previous", "Import" und "Export".

|Gehe zu Feld|Batch-Check-in|Adress-Editor|Zuordnungs-Editor|
|-|-|-|-|
|![Symbol "Gehe zu Feld"](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Symbol für Überprüfung&#45;in Batch](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Symbol "Adress-Editor"](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Symbol "Zuordnungs-Editor"](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Dunkel Gold wird hauptsächlich für den Modifizierer "New" verwendet.

|Neues Projekt|Neues Diagramm erstellen|Neuer Komponenten Test|Neues Listenelement|
|-|-|-|-|
|![Symbol "Neues Projekt"](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Symbol "Neues Diagramm erstellen"](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Symbol "Neuer Komponententest"](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Symbol "Neues Listenelement"](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Spezialfälle
 In besonderen Fällen kann ein farbiger Aktionsmodifizierer unabhängig als eigenständiges Symbol verwendet werden. Die Farbe, die für das Symbol verwendet wird, spiegelt die Aktionen wider, denen das Symbol zugeordnet ist. Diese Verwendung ist auf eine kleine Teilmenge von Symbolen beschränkt, einschließlich:

|Ausführen|Beenden|Löschen|Speichern|Rückwärts navigieren|
|-|-|-|-|-|
|![Symbol "Ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Stoppsymbol](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Symbol "Löschen"](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Symbol „Speichern“](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Symbol "Rückwärts navigieren"](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Code Hierarchie Palette

#### <a name="folder"></a>Ordner

|Verbrauch|name|Wert (alle Designs)|Swatch|Beispiel|
|-----------|----------|--------------------------|------------|-------------|
|Ordner|Ordner|DCB67A/220.182.122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Symbol "Ordnerfarbe"](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen
 Jede der in Visual Studio verfügbaren allgemeinen Sprachen oder Plattformen weist eine zugehörige Farbe auf. Diese Farben werden für das Basis Symbol oder für sprach Modifizierer verwendet, die in der oberen rechten Ecke der Verbund Symbole angezeigt werden.

|Verbrauch|name|Wert (alle Designs)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095d7/0149.215|![Muster 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Cpp-lila|9b4f 96/155, 79150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS-grün (VS-Aktion grün)|388a34/56138, 52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS rot|BD1E2D/189, 30, 45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS-lila|672878/103, 40120|![Muster 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Orangefarbenes js|F16421/241100, 33|![Muster F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (VS-Aktion blau)|00539c/0, 83156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06/224, 76, 6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY-grün|879636/135150, 54|![Muster 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele für Symbole mit sprachenmodifiziererwerten

|VB|C#|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![C-&#35; Symbol](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![C-&#43;&#43; Symbol](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35; Symbol](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![JavaScript-Symbol](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Python-Symbol](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|-|
|![HTML-Symbol](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF-Symbol](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS-Symbol](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense-Symbole verwenden eine exklusive Farbpalette. Diese Farben werden verwendet, um Benutzern zu helfen, schnell zwischen den verschiedenen Elementen in der IntelliSense-Popup Liste zu unterscheiden.

|Verbrauch|name|Wert (alle Designs)|Swatch|
|-----------|----------|--------------------------|------------|
|Klasse, Ereignis|VS-Aktion Orange|C27D1A/194125, 26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Erweiterungsmethode, Methode, Modul, Delegat|VS-Aktion, lila|652d90/101, 45144|![Muster 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Feld, enum-Element, Makro, Struktur, Union-Werttyp, Operator, Schnittstelle|VS-Aktion blau|00539c/0, 83156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS-Aktion grün|388a34/56138, 52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Konstante, Ausnahme, enum-Element, Zuordnung, Kartenelement, Namespace, Vorlage, Typdefinition|Hintergrund (vs BG)|424242/66, 66, 66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Beispiele für IntelliSense-Symbole

|Klasse|Privates Ereignis|Delegat|Methoden Friend|Feld|
|-|-|-|-|-|
|![Symbol für IntelliSense-Klasse](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Symbol für privates IntelliSense-Ereignis](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Symbol für IntelliSense-Methode "Friend"](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Symbol "Feld"](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Geschütztes enum-Element|Object|Vorlage|Ausnahme Verknüpfung|
|-|-|-|-|
|![Symbol für geschütztes IntelliSense-Enum-Element](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Symbol für IntelliSense-Ausnahmeverknüpfung](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Benachrichtigungen
 Benachrichtigungen in Visual Studio werden verwendet, um den Status anzugeben. In der Benachrichtigungs Palette werden die folgenden vier Farben verwendet, sowie die Füll Optionen schwarz oder weiß, um Benachrichtigungen mit den folgenden Status Ebenen zu definieren.

|Verbrauch|name|Wert (alle Designs)|Swatch|
|-----------|----------|--------------------------|------------|
|Status: neutral|Benachrichtigung blau (vs Blue)|1ba1e2/27.161.226|![Muster 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Status: positiv|Benachrichtigungs grün (vs grün)|339933/51153, 51|![Muster 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Status: negativ|Benachrichtigung rot (vs rot)|E51400/229, 20, 0|![Muster E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Status: Warnung|Benachrichtigung gelb (vs Orange)|FFCC00/255204, 0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Vordergrund Füllung|Benachrichtigung schwarz (schwarz)|000000/0, 0, 0|![Muster &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Vordergrund Füllung|Benachrichtigung weiß (weiß)|FFFFFF/255.255.255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Beispiele für Benachrichtigungs Symbole

|Warnung|Warnung|Abgeschlossen|Beenden|
|-|-|-|-|
|![Warnungssymbol](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Warnungssymbol](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Symbol "Abgeschlossen"](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Stoppsymbol](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|