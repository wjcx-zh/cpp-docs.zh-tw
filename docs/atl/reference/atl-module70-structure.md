---
title: _ATL_MODULE70 結構 |Microsoft 文件
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
ms.openlocfilehash: 3a374ee01387c576a5d1a727857badc7ef7139ad
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
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
 `cbSize`  
 用來進行版本控制的結構大小。  
  
 `m_nLockCnt`  
 參考計數決定多久模組應該保持作用中。  
  
 **m_pTermFuncs**  
 已登錄為 ATL 關閉時呼叫的追蹤函式。  
  
 **m_csStaticDataInitAndTypeInfo**  
 用來協調在多執行緒的情況下的內部資料的存取權。  
  
## <a name="remarks"></a>備註  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)定義為 typedef 的`_ATL_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
  [類別和結構](../../atl/reference/atl-classes.md)







