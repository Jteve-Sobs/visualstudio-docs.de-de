---
title: Setwef ProcessID-Methode
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537331"
---
# <a name="setwefprocessid-method"></a>Setwef ProcessID-Methode
  Stellt den Prozess Bezeichner bereit, mit dem WEF-Inhalte (Web Extensions Framework) ausgeführt werden.

## <a name="syntax"></a>Syntax

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwProcessId*|Der Prozess Bezeichner, der zum Ausführen von WEF-Inhalten verwendet wird.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Hinweise
 Diese Methode muss aufgerufen werden, nachdem der WEF-Inhalts Prozess erstellt wurde, aber bevor WEF-Inhalte ausgeführt werden.

 Wenn Sie möchten, dass die Entwicklungsumgebung einen Debugger an den WEF-Inhalts Prozess anfügt, muss die Umgebung diesen Vorgang in der Implementierung dieser Methode ausführen.
