---
title: IDebugBoundBreakpoint2::GetPendingBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4037cff1e080b4af97dbc56de4802f6f73504649
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735492"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
Ruft den ausstehenden Haltepunkt ab, von dem aus der angegebene gebundene Haltepunkt erstellt wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPendingBreakpoint( 
    IDebugPendingBreakpoint2** ppPendingBreakpoint
);
```

```csharp
int GetPendingBreakpoint( 
    out IDebugPendingBreakpoint2 ppPendingBreakpoint
);
```

## <a name="parameters"></a>Parameter
`ppPendingBreakpoint`\
[out] Gibt das [IDebugPendingBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) zurück, das den ausstehenden Haltepunkt darstellt, der zum Erstellen dieses gebundenen Haltepunkts verwendet wurde.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Ein ausstehender Haltepunkt kann als eine Sammlung aller erforderlichen Informationen betrachtet werden, die erforderlich sind, um einen Haltepunkt an Code zu binden, der auf ein oder mehrere Programme angewendet werden kann.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CBoundBreakpoint` Methode für ein einfaches Objekt implementiert wird, das die [IDebugBoundBreakpoint2-Schnittstelle](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) verfügbar macht.

```
HRESULT CBoundBreakpoint::GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBreakpoint)
{
    HRESULT hr;

    // Check for valid IDebugPendingBreakpoint2 interface pointer.
    if (ppPendingBreakpoint)
    {
        // Be sure that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugPendingBreakpoint2 interface.
            hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,
                                              (void**)ppPendingBreakpoint);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
