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
ms.openlocfilehash: 0b636d328852daf821269230aae443cef084578b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299708"
---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 結構

ATL 中的視窗化程式碼使用

## <a name="syntax"></a>語法

```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構，用來進行版本設定的大小。

`m_csWindowCreate`<br/>
用來序列化存取視窗註冊碼。 供內部使用 ATL

`m_pCreateWndList`<br/>
用來繫結至其物件的 windows。 供內部使用 ATL

`m_rgWindowClassAtoms`<br/>
用來追蹤視窗類別註冊，讓它們可以適當地取消註冊，在終止。 供內部使用 ATL

## <a name="remarks"></a>備註

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)定義的 typedef 的`_ATL_WIN_MODULE70`。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
