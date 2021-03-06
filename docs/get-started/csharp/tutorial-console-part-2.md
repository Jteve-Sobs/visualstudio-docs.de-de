---
title: 'Tutorial: Erweitern einer einfachen C#-Konsolen-App'
description: Hier erfahren Sie anhand einer exemplarischen Vorgehensweise, wie Sie eine C#-Konsolen-App in Visual Studio erstellen.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aae83c43a106fd68b03a83124ad2ddcea4652c8d
ms.sourcegitcommit: c620d59578db1b89f80e64ae04b4898bc4ab292d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87375926"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Tutorial: Erweitern einer einfachen C#-Konsolen-App

In diesem Tutorial erfahren Sie, wie Sie Visual Studio verwenden, um die Konsolen-App zu erweitern, die Sie im ersten Teil erstellt haben. Dabei lernen Sie einige Features von Visual Studio kennen, die Sie Ihre Produktivität als Entwickler steigern, z. B. erweiterter Editor- und Debugfeatures.

Wenn Sie den [ersten Teil](tutorial-console.md) dieser Reihe abgeschlossen haben, verfügen Sie bereits über die Calculator-Konsolen-App.  Sie können damit beginnen, das Projekt aus einem GitHub-Repository zu öffnen, um Teil 1 zu überspringen. Die C#-App „Calculator“ finden Sie im Repository [vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples). Sie können also einfach die Schritte im [Tutorial: Öffnen eines Projekts aus einem Repository](../tutorial-open-project-from-repo.md) ausführen, um zu beginnen.

## <a name="add-a-new-project"></a>Neues Projekt hinzufügen

In der Praxis umfasst Code viele Projekte, die in einer Projektmappe zusammenarbeiten. Als Nächstes fügen Sie ein weiteres Projekt zur Calculator-App hinzu. Dabei handelt es sich um eine Klassenbibliothek, die einige der Rechnerfunktionen bereitstellt.

1. In Visual Studio können Sie den allgemeinen Menübefehl **Datei** > **Hinzufügen** > **Neues Projekt** verwenden, um ein neues Projekt hinzuzufügen, jedoch können Sie auch mit der rechten Maustaste auf den Namen des vorhandenen Projekts klicken (der „Projektknoten“), um das Kontextmenü des Projekts zu öffnen. Dieses Kontextmenü enthält mehrere Möglichkeiten, mit denen Sie Funktionen zu Ihren Projekten hinzufügen können. Klicken Sie also mit der rechten Maustaste auf Ihren Projektknoten im **Projektmappen-Explorer**, und wählen Sie dann **Hinzufügen** > **Neues Projekt** aus.

1. Wählen Sie die C#-Projektvorlage **Klassenbibliothek (.NET Standard)** aus.

   ![Screenshot: Auswahl der Projektvorlage „Klassenbibliothek“](media/vs-2019/calculator2-add-project-dark.png)

1. Geben Sie den Projektnamen **CalculatorLibrary** ein, und klicken Sie dann auf **Erstellen**. Visual Studio erstellt das neue Projekt und fügt es zur Projektmappe hinzu.

   ![Screenshot: Projektmappen-Explorer mit hinzugefügtem Klassenbibliotheksprojekt „CalculatorLibrary“](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Benennen Sie die Datei *Class1.cs* in **CalculatorLibrary.cs** um. Sie können im **Projektmappen-Explorer** auf den Namen klicken, um diesen zu ändern, oder klicken Sie mit der rechten Maustaste auf den Namen, und wählen Sie dann **Umbenennen** aus, oder drücken Sie **F2**.

   Möglicherweise werden Sie gefragt, ob Sie Verweise auf `Class1` in der Datei umbenennen möchten. Es spielt keine Rolle, wie Sie antworten, da Sie den Code in einem zukünftigen Schritt ersetzen.

1. Jetzt müssen Sie einen Projektverweis hinzufügen, damit das erste Projekt die APIs nutzen kann, die von der neuen Klassenbibliothek zur Verfügung gestellt werden.  Klicken Sie mit der rechten Maustaste auf den Knoten **Verweise** im ersten Projekt, und wählen Sie dann **Projektverweis hinzufügen** aus.

   ![Screenshot: Menüelement „Projektverweis hinzufügen“](media/vs-2019/calculator2-add-project-reference-dark.png)

   Das Dialogfeld **Verweis-Manager** wird angezeigt. Mithilfe dieses Dialogfelds können Sie Verweise auf andere Projekte sowie Assemblys und COM DLLs hinzufügen, die Ihre Projekte benötigen.

   ![Screenshot: Dialogfeld „Verweis-Manager“](media/vs-2019/calculator2-ref-manager-dark.png)

1. Aktivieren Sie im Dialogfeld **Verweis-Manager** das Kontrollkästchen für das Projekt **CalculatorLibrary**, und klicken Sie dann auf **OK**.  Der Projektverweis wird unter dem Knoten **Projekte** im **Projektmappen-Explorer** angezeigt.

   ![Screenshot: Projektmappen-Explorer mit Projektverweis](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. Wählen Sie in der Datei *Program.cs* die Klasse `Calculator` und ihren gesamten Code aus, und drücken Sie **STRG+X**, um diesen aus der Datei auszuschneiden. Fügen Sie den Code dann in **CalculatorLibrary** in der Datei *CalculatorLibrary.cs* in den Namespace `CalculatorLibrary` ein. Erstellen Sie dann die Calculator-Klasse `public`, um ihn außerhalb der Bibliothek zur Verfügung zu stellen. Der Code in der Datei *CalculatorLibrary.cs* sollte nun dem folgenden Code ähneln:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
                switch (op)
                {
                    case "a":
                        result = num1 + num2;
                        break;
                    case "s":
                        result = num1 - num2;
                        break;
                    case "m":
                        result = num1 * num2;
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. Das erste Projekt enthält einen Verweis, jedoch wird ein Fehler angezeigt, der angibt, dass der Calculator.DoOperation-Aufruf nicht aufgelöst werden kann. Das liegt daran, dass sich CalculatorLibrary in einem anderen Namespace befindet. Fügen Sie also den Namespace `CalculatorLibrary` hinzu, damit Sie über einen vollqualifizierten Verweis verfügen.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Versuchen Sie stattdessen, eine using-Anweisung am Anfang der Datei hinzuzufügen:

   ```csharp
   using CalculatorLibrary;
   ```

   Durch diese Änderung sollten Sie dazu in der Lage sein, den CalculatorLibrary-Namespace aus der Aufrufsite zu entfernen, jedoch liegt nun eine Mehrdeutigkeit vor. Ist `Calculator` die Klasse in CalculatorLibrary oder ist „Calculator“ der Namespace?  Benennen Sie den Namespace `CalculatorProgram` um, um diese Mehrdeutigkeit aufzulösen.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Referenzieren von .NET-Bibliotheken: Schreiben in ein Protokoll

1. Angenommen, Sie möchten nun ein Protokoll aller Vorgänge hinzufügen und dieses in eine Textdatei schreiben. Die .NET-Klasse `Trace` stellt diese Funktionalität bereit. (Dies eignet auch für grundlegende Debugverfahren mit Ablaufverfolgung.)  Die Trace-Klasse befindet sich in System.Diagnostics, daher fügen Sie zunächst eine using-Anweisung hinzu:

   ```csharp
   using System.Diagnostics;
   ```

1. Dementsprechend, wie die Trace-Klasse verwendet wird, müssen Sie einen Verweis auf die Klasse verwenden, der einem Filestream zugeordnet ist. Das bedeutet, der Rechner würde als Objekt besser funktionieren, also fügen Sie einen Konstruktor hinzu.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Außerdem müssen Sie die statische Methode `DoOperation` in eine Membermethode ändern.  Fügen Sie also Ausgaben zu jeder Berechnung für das Protokoll hinzu, sodass DoOperation dem folgenden Code ähnelt:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Wenn Sie nun wieder die Datei „Program.cs“ öffnen, wird der statische Aufruf mit einer roten Wellenlinie gekennzeichnet. Erstellen Sie eine `calculator`-Variable, indem Sie die folgende Zeile unmittelbar vor der while-Schleife hinzufügen, um dies zu beheben:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ändern Sie außerdem die Aufrufsite für `DoOperation` wie folgt:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Führen Sie das Programm noch mal aus. Klicken Sie anschließend mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Ordner im Datei-Explorer öffnen** aus. Navigieren Sie dann im Datei-Explorer nach unten zum Ausgabeordner. Dabei handelt es sich möglicherweise um *bin/Debug/netcoreapp3.1*. Öffnen Sie die Datei *calculator.log*.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Hinzufügen eines NuGet-Pakets: Schreiben in eine JSON-Datei

1. Angenommen Sie möchten die Vorgänge nun in einem JSON-Format ausgeben. Dabei handelt es sich um ein beliebtes und portierbares Format zum Speichern von Objektdaten. Zum Implementieren dieser Funktionalität müssen Sie das NuGet-Paket „Newtonsoft.Json“ referenzieren. NuGet-Pakete sind die primäre Methode zur Verteilung von .NET-Klassenbibliotheken. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** für das CalculatorLibrary-Projekt, und wählen Sie dann **NuGet-Pakete verwalten** aus.

   ![Screenshot: „NuGet-Pakete verwalten“ im Kontextmenü](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Daraufhin wird der NuGet-Paket-Manager geöffnet.

   ![Screenshot: NuGet-Paket-Manager](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Suchen Sie nach dem Paket „Newtonsoft.Json“, und klicken Sie auf **Installieren**.

   ![Screenshot: Informationen zum NuGet-Paket „Newtonsoft“](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Das Paket wird heruntergeladen und zu Ihrem Projekt hinzugefügt, außerdem wird im **Projektmappen-Explorer** im Knoten „Verweise“ ein neuer Eintrag angezeigt.

1. Fügen Sie eine using-Anweisung für das Paket „Newtonsoft.Json“ am Anfang der Datei *CalculatorLibrary.cs* hinzu.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Ersetzen Sie nun den Konstruktor für Calculator durch den folgenden Code, und erstellen Sie das Memberobjekt „JsonWriter“:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Ändern Sie die `DoOperation`-Methode, um den JSON-Writer-Code hinzuzufügen:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Sie müssen eine Methode hinzufügen, um die JSON-Syntax zu beenden, sobald der Benutzer damit fertig ist, Vorgangsdaten einzugeben.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. Fügen Sie außerdem am Ende der Datei *Program.cs* einen Aufruf zum Beenden hinzu.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Erstellen Sie die App, und führen Sie sie aus. Nachdem Sie einige Vorgänge eingegeben haben, schließen Sie die App ordnungsgemäß mithilfe des Befehls „n“.  Öffnen Sie nun die Datei „consolelog.json“. Dort sollten Sie etwas sehen, das dem folgenden Beispiel ähnelt:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wenn Sie weitere Informationen erhalten möchten, fahren Sie mit den folgenden Tutorials fort.

> [!div class="nextstepaction"]
> [C#-Tutorials](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Übersicht über die Visual Studio-IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Siehe auch

* [C#-IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Tutorial: Debuggen von C#-Code mit Visual Studio](tutorial-debugger.md)
