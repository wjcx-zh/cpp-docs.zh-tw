---
title: _ATL_MODULE70 結構
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8d39cdd281e09cdfe09546627aa630a11d12464e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168562"
---
# <a name="_atl_module70-structure"></a>_ATL_MODULE70 結構

包含每個 ATL 模組所使用的資料。

## <a name="syntax"></a>語法

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構的大小，用於版本控制。

`m_nLockCnt`<br/>
參考計數，用以判斷模組應該保持運作的時間長度。

`m_pTermFuncs`<br/>
追蹤已註冊要在 ATL 關閉時呼叫的函式。

`m_csStaticDataInitAndTypeInfo`<br/>
用來協調多執行緒情況下對內部資料的存取。

## <a name="remarks"></a>備註

[_ATL_MODULE](atl-typedefs.md#_atl_module)定義為的`_ATL_MODULE70`typedef。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
