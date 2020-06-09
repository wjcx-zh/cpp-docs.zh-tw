---
title: COM 介面進入點
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 132dd7394119081dcaeb098c2088782ff5d40ae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619333"
---
# <a name="com-interface-entry-points"></a>COM 介面進入點

若為 COM 介面的成員函式，請在 `METHOD_PROLOGUE` 呼叫匯出介面的方法時，使用宏來維護適當的全域狀態。

通常 `CCmdTarget` 衍生物件所實作介面的成員函式，已使用此巨集來提供 `pThis` 指標的自動初始化。 例如：

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

如需其他資訊，請參閱 MFC/OLE 執行[技術提示 38](tn038-mfc-ole-iunknown-implementation.md) `IUnknown` 。

`METHOD_PROLOGUE` 巨集定義如下：

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

與管理全域狀態相關巨集的部分是：

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

在此運算式中，會假設*m_pModuleState*是包含物件的成員變數。 將物件具現話化時，運算式會由 `CCmdTarget` 基底類別實作，並且由 `COleObjectFactory` 初始化為適當的值。

## <a name="see-also"></a>另請參閱

[管理 MFC 模組的狀態資料](managing-the-state-data-of-mfc-modules.md)
