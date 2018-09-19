---
title: _ATL_COM_MODULE70 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cfa52749f6789ef8bfe65f9bdcdf5238923216f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019370"
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 結構

ATL 中的 COM 相關程式碼使用

## <a name="syntax"></a>語法

```
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
結構，用來進行版本設定的大小。

`m_hInstTypeLib`<br/>
型別程式庫，此模組控制代碼的執行個體。

`m_ppAutoObjMapFirst`<br/>
指出此模組的物件對應項目開頭的陣列元素的位址。

`m_ppAutoObjMapLast`<br/>
指出物件的對應項目，此模組結束陣列元素的位址。

`m_csObjMap`<br/>
將序列化物件的對應項目存取的重要區段。 供內部使用 ATL

## <a name="remarks"></a>備註

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)定義為 _ATL_COM_MODULE70 的 typedef。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)

