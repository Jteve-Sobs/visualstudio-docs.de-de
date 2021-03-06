---
title: 'Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579438"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen

Jetzt sind Sie bereit, die anderen vier Methoden abzuschließen. Sie können diesen Code zwar kopieren und einfügen, aber um bei diesem Lernprogramm den größtmöglichen Lerneffekt zu erzielen, sollten Sie den Code eingeben und IntelliSense verwenden.

Mit diesem Code wird den Schaltflächen die Funktionalität hinzugefügt, die Sie zuvor hinzugefügt haben. Ohne diesen Code haben die Schaltflächen keine Funktion. In den <xref:System.Windows.Forms.Control.Click>-Ereignissen der Schaltflächen wird Code verwendet (und im Kontrollkästchen wird das <xref:System.Windows.Forms.CheckBox.CheckedChanged>-Ereignis verwendet), damit unterschiedliche Aufgaben ausgeführt werden, wenn die Steuerelemente aktiviert werden. Beispielsweise löscht das Ereignis `clearButton_Click` (oder `ClearButton_Click`), das ausgelöst wird, wenn Sie auf **Clear the picture** (Bild löschen) klicken, das Bild, indem die **Image**-Eigenschaft auf **NULL** (oder **Nichts**) festgelegt wird. Alle Ereignisse im Code enthalten Kommentare, in denen der Zweck des Codes erklärt wird.

> [!TIP]
> Bewährt hat sich folgende Methode: Kommentieren Sie stets Ihren Code. Kommentare stellen Informationen für andere Personen bereit, und Sie sollten sich die Zeit nehmen, den Code verständlich zu machen. Der gesamte Inhalt von Kommentarzeilen wird von der App ignoriert. In C# kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile zwei Schrägstriche (//) eingegeben. In Visual Basic kommentieren Sie eine Zeile, indem Sie zu Beginn der Zeile ein einfaches Anführungszeichen (') einfügen.

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen

Fügen Sie der Codedatei **Form1** (*Form1.cs* oder *Form1.vb*) den folgenden Code hinzu.

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Der Code zeigt möglicherweise keine Binnenmajuskel an.

## <a name="next-steps"></a>Nächste Schritte

* Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 11: Ausführen Ihrer App und Ausprobieren weiterer Features](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Siehe auch

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
