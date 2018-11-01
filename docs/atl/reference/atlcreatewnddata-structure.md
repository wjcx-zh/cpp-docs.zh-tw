---
title: _AtlCreateWndData 結構
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 860d5772279d0ca0581a8cac1e0ef224f829586d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534182"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData 結構

此結構包含在 ATL 中的視窗化程式碼中的類別執行個體資料

## <a name="syntax"></a>語法

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>成員

`m_pThis`<br/>
**這**用來取得視窗程序中的存取權的類別執行個體的指標。

`m_dwThreadID`<br/>
目前的類別執行個體的執行緒 ID。

`m_pNext`<br/>
下一個指標`_AtlCreateWndData`物件。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)

