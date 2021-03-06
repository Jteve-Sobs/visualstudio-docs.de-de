---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734455"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Erstellt einen Enumerator für die Konstruktoren für diese Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`cMatch`\
[in] Ein Wert [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) aus der CONSTRUCTOR_ENUM-Enumeration, der den Typ der Konstruktoren für die Enumeration angibt.

`ppEnum`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der Konstruktoren darstellt. Gibt einen NULL-Wert zurück, wenn keine Konstruktoren vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Konstruktoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element der Enumeration ist ein [IDebugMethodField-Objekt,](../../../extensibility/debugger/reference/idebugmethodfield.md) das eine Konstruktormethode beschreibt.

 Die Liste der Konstruktoren enthält in der Regel nicht die Standardkonstruktoren, die von einem Compiler bereitgestellt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
