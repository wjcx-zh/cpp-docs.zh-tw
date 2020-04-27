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
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168536"
---
# <a name="_atlcreatewnddata-structure"></a>_AtlCreateWndData 結構

此結構包含 ATL 中的視窗化程式碼中的類別實例資料。

## <a name="syntax"></a>語法

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>成員

`m_pThis`<br/>
**這個**指標用來取得視窗程式中類別實例的存取權。

`m_dwThreadID`<br/>
目前類別實例的執行緒識別碼。

`m_pNext`<br/>
下一個`_AtlCreateWndData`物件的指標。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
