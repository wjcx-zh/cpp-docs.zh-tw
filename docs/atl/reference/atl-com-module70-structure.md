---
title: _ATL_COM_MODULE70 結構
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168627"
---
# <a name="_atl_com_module70-structure"></a>_ATL_COM_MODULE70 結構

在 ATL 中由 COM 相關的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構的大小，用於版本控制。

`m_hInstTypeLib`<br/>
此模組之類型程式庫的控制碼實例。

`m_ppAutoObjMapFirst`<br/>
陣列元素的位址，指出此模組的物件對應專案的開頭。

`m_ppAutoObjMapLast`<br/>
陣列元素的位址，指出此模組的物件對應專案結尾。

`m_csObjMap`<br/>
序列化物件對應項存取的重要區段。 由 ATL 在內部使用。

## <a name="remarks"></a>備註

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)定義為 _ATL_COM_MODULE70 的 typedef。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)
