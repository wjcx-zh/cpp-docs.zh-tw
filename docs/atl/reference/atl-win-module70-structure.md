---
title: _ATL_WIN_MODULE70 結構
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168549"
---
# <a name="_atl_win_module70-structure"></a>_ATL_WIN_MODULE70 結構

由 ATL 中的視窗化程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構的大小，用於版本控制。

`m_csWindowCreate`<br/>
用來序列化對視窗註冊程式碼的存取。 由 ATL 在內部使用。

`m_pCreateWndList`<br/>
用來將視窗系結至其物件。 由 ATL 在內部使用。

`m_rgWindowClassAtoms`<br/>
用來追蹤視窗類別註冊，使其在終止時可以適當地取消註冊。 由 ATL 在內部使用。

## <a name="remarks"></a>備註

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)定義為的`_ATL_WIN_MODULE70`typedef。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
