---
title: Ausdrücke im Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301416"
---
# <a name="expressions-in-the-debugger"></a>Ausdrücke im Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Debugger beinhaltet eine Ausdrucksauswertung, die aktiv wird, wenn Sie einen Ausdruck in das Dialogfeld **Schnellüberwachung** , in das Fenster **Überwachen** oder in das Fenster **Direkt** eingeben. Die Ausdruckauswertung ist auch im Fenster **Haltepunkte** sowie an vielen anderen Stellen im Debugger aktiv.  
  
 Die folgenden Abschnitte enthalten Informationen zu Ausdrücken in verschiedenen Sprachen.  
  
## <a name="f-expressions-are-not-supported"></a>F#-Ausdrücke werden nicht unterstützt.  
 F#-Ausdrücke werden nicht erkannt. Wenn Sie F#-Code debuggen, müssen Sie die Ausdrücke vor dem Eingeben in ein Debuggerfenster oder ein Dialogfeld in C#-Syntax übersetzen. Wenn Sie Ausdrücke aus F# in C# übersetzen, beachten Sie, dass C# den `==` -Operator für Gleichheitstests verwendet, wohingegen F# ein einfaches Gleichheitszeichen ( `=`) verwendet.  
  
## <a name="c-expressions"></a>C++-Ausdrücke  
 Informationen zum Verwenden von Kontextoperatoren mit Ausdrücken in C++ finden Sie unter [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nicht unterstützte Ausdrücke in C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktoren, Destruktoren und Konvertierungen  
 Einen Konstruktor oder Destruktor für ein Objekt können Sie weder explizit noch implizit aufrufen. Mit folgendem Ausdruck wird ein Konstruktor beispielsweise explizit aufgerufen, was eine Fehlermeldung zur Folge hat:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Sie können keine Konvertierungsfunktion aufrufen, wenn es sich beim Ziel der Konvertierung um eine Klasse handelt. Eine solche Konvertierung impliziert die Erstellung eines Objekts. Wenn `myFraction` beispielsweise eine Instanz von `CFraction`ist, durch die der Konvertierungsfunktionsoperator `FixedPoint`definiert wird, verursacht der folgende Ausdruck einen Fehler:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Sie können den new- oder delete-Operator nicht aufrufen. Beispielsweise wird der folgende Ausdruck nicht unterstützt:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Präprozessormakros  
 Präprozessormakros werden im Debugger nicht unterstützt. Wenn beispielsweise eine Konstante `VALUE` als `#define VALUE 3`deklariert wird, können Sie `VALUE` im Fenster **Überwachen** nicht verwenden. Um diese Einschränkung zu vermeiden, sollten Sie `#define`nach Möglichkeit durch Enumerationen und Funktionen ersetzen.  
  
### <a name="using-namespace-declarations"></a>"using namespace"-Deklarationen  
 Sie können keine `using namespace` -Deklarationen verwenden.  Um auf einen Typnamen oder eine Variable außerhalb des aktuellen Namespace zugreifen zu können, müssen Sie den vollqualifizierten Namen verwenden.  
  
### <a name="anonymous-namespaces"></a>Anonyme Namespaces  
 Anonyme Namespaces werden nicht unterstützt. Bei folgendem Code können Sie `test` im Fenster "Überwachen" nicht hinzufügen:  
  
```cpp  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Verwenden von systeminternen Debuggerfunktionen zum Beibehalten des Status  
 Die systeminternen Debugger-Funktionen geben Ihnen eine Möglichkeit, zum Aufruf bestimmter C/C++-Funktionen in Ausdrücken ohne den Zustand der Anwendung zu ändern.  
  
 Systeminterne Debugger-Funktionen:  
  
- Diese sind garantiert sicher: durch das Ausführen einer systeminternen Debugger-Funktion wird der Prozess, der debuggt wird, nicht beschädigt.  
  
- Sie sind in allen Ausdrücken zulässig, sogar in Szenarien, in denen Nebeneffekte und Funktionsauswertung nicht gestattet ist.  
  
- Sie arbeiten in Szenarien, in denen reguläre Funktionsaufrufe nicht möglich sind, z. B. das Debuggen eines Minidumps.  
  
  Mit systeminternen Debugger-Funktionen kann die Auswertung von Ausdrücken bequemer werden. Beispielsweise ist `strncmp(str, “asd”)` viel einfacher in einer Haltepunktbedingung zu schreiben als `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Bereich|Systeminterne Funktionen|  
|----------|-------------------------|  
|**Zeichenfolgenlänge**|strlen, wcslen, strnlen, wcsnlen|  
|**Zeichenfolgenvergleich**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Zeichenfolgensuche**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Für diese Funktionen muss der Prozess, der debuggt wird, auf Windows. 8 ausgeführt werden. Das Debuggen von Dumpdateien, die von einem Windows 8-Gerät generiert werden, erfordert auch, dass auf dem Visual Studio-Computer Windows 8 ausgeführt wird. Wenn Sie für ein Windows 8-Gerät Remotedebuggen durchführen, kann auf dem Visual Studio-Computer Windows 7 ausgeführt werden.|  
|**Sonstiges**|__log2<br /><br /> Gibt die Protokollbasis 2 einer angegebenen ganzen Zahl auf die nächste kleinere ganze Zahl gerundet zurück.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI – Nicht unterstützte Ausdrücke  
  
- Typumwandlungen mit Zeigern oder benutzerdefinierten Typumwandlungen werden nicht unterstützt.  
  
- Vergleiche und Zuweisungen von Objekten werden nicht unterstützt.  
  
- Überladene Operatoren und überladene Funktionen werden nicht unterstützt.  
  
- Boxing und Unboxing werden nicht unterstützt.  
  
- Der`Sizeof` -Operator wird nicht unterstützt.  
  
## <a name="c---unsupported-expressions"></a>C# – Nicht unterstützte Ausdrücke  
  
### <a name="dynamic-objects"></a>Dynamische Objekte  
 Sie können Variablen in Debuggerausdrücken verwenden, die statisch als dynamisch typisiert sind. Wenn Objekte, die die <xref:System.Dynamic.IDynamicMetaObjectProvider> implementieren, im Überwachungsfenster ausgewertet werden, wird ein dynamischer Ansichtsknoten hinzugefügt. Der dynamische Ansichtsknoten zeigt Member an, ermöglicht aber keine Bearbeitung der Memberwerte.  
  
 Die folgenden Funktionen dynamischer Objekte werden nicht unterstützt:  
  
- Die zusammengesetzten Operatoren `+=`, `-=`, `%=`, `/=`und `*=`  
  
- Viele Umwandlungen, einschließlich numerischer Umwandlungen und Typargumentumwandlungen  
  
- Methodenaufrufe mit mehr als zwei Argumenten  
  
- Eigenschaftengetter mit mehr als zwei Argumenten  
  
- Eigenschaftensetter mit Argumenten  
  
- Zuweisen zu einem Indexer  
  
- Boolesche Operatoren `&&` und `||`  
  
### <a name="anonymous-methods"></a>Anonyme Methoden  
 Die Erstellung neuer anonymer Methoden wird nicht unterstützt.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic – Nicht unterstützte Ausdrücke  
  
### <a name="dynamic-objects"></a>Dynamische Objekte  
 Sie können Variablen in Debuggerausdrücken verwenden, die statisch als dynamisch typisiert sind. Wenn Objekte, die die <xref:System.Dynamic.IDynamicMetaObjectProvider> implementieren, im Überwachungsfenster ausgewertet werden, wird ein dynamischer Ansichtsknoten hinzugefügt. Der dynamische Ansichtsknoten zeigt Member an, ermöglicht aber keine Bearbeitung der Memberwerte.  
  
 Die folgenden Funktionen dynamischer Objekte werden nicht unterstützt:  
  
- Die zusammengesetzten Operatoren `+=`, `-=`, `%=`, `/=`und `*=`  
  
- Viele Umwandlungen, einschließlich numerischer Umwandlungen und Typargumentumwandlungen  
  
- Methodenaufrufe mit mehr als zwei Argumenten  
  
- Eigenschaftengetter mit mehr als zwei Argumenten  
  
- Eigenschaftensetter mit Argumenten  
  
- Zuweisen zu einem Indexer  
  
- Boolesche Operatoren `&&` und `||`  
  
### <a name="local-constants"></a>Lokale Konstanten  
 Lokale Konstanten werden nicht unterstützt.  
  
### <a name="import-aliases"></a>Importaliase  
 Importaliase werden nicht unterstützt.  
  
### <a name="variable-declarations"></a>Variablendeklarationen  
 Neue Variablen können in Debuggerfenstern nicht explizit deklariert werden. Allerdings sind Zuweisungen neuer impliziter Variablen im Fenster **Direkt** möglich. Diese impliziten Variablen sind auf die Debugsitzung beschränkt und können von außerhalb des Debuggers nicht aufgerufen werden. Die Anweisung `o = 5` beispielsweise erstellt implizit eine neue `o` -Variable und weist dieser den Wert 5 zu. Solche impliziten Variablen sind vom Typ **Object** , sofern der Typ nicht durch den Debugger abgeleitet werden kann.  
  
### <a name="unsupported-keywords"></a>Nicht unterstützte Schlüsselwörter  
  
- `AddressOf`  
  
- `End`  
  
- `Error`  
  
- `Exit`  
  
- `Goto`  
  
- `On Error`  
  
- `Resume`  
  
- `Return`  
  
- `Select/Case`  
  
- `Stop`  
  
- `SyncLock`  
  
- `Throw`  
  
- `Try/Catch/Finally`  
  
- `With`  
  
- Schlüsselwörter der Namespace- oder Modulebene, wie `End Sub` oder `Module`.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatbezeichner in C++](../debugger/format-specifiers-in-cpp.md)   
 [Kontextoperator (C++)](../debugger/context-operator-cpp.md)   
 [Formatbezeichner in C #](../debugger/format-specifiers-in-csharp.md)   
 [Pseudovariablen](../debugger/pseudovariables.md)
