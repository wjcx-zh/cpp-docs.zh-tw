---
title: "_ATL_MODULE70 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: ea1d87d3d500fc08f3da16de6820ca003e899419
ms.lasthandoff: 02/24/2017

---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 結構
包含每一個 ATL 模組所使用的資料。  
  
## <a name="syntax"></a>語法  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>Members  
 `cbSize`  
 使用版本控制的結構大小。  
  
 `m_nLockCnt`  
 參考計數來決定多久模組應該保持作用中。  
  
 **m_pTermFuncs**  
 追蹤已登錄為 ATL 關機時呼叫的函式。  
  
 **m_csStaticDataInitAndTypeInfo**  
 用來協調多執行緒情況中的內部資料的存取權。  
  
## <a name="remarks"></a>備註  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)定義為 typedef 的`_ATL_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)








