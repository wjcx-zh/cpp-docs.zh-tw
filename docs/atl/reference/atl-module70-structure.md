---
title: _ATL_MODULE70 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f84b90613bcf542a9ace44505565951819fcaa91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108439"
---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 結構

包含每個 ATL 模組所使用的資料。

## <a name="syntax"></a>語法

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構，用來進行版本設定的大小。

`m_nLockCnt`<br/>
參考計數來決定多久模組應該保持作用中。

`m_pTermFuncs`<br/>
追蹤已登錄為 ATL 關閉時呼叫的函式。

`m_csStaticDataInitAndTypeInfo`<br/>
用來協調多執行緒的情況下的內部資料的存取權。

## <a name="remarks"></a>備註

[_ATL_MODULE](atl-typedefs.md#_atl_module)定義的 typedef 的`_ATL_MODULE70`。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)

