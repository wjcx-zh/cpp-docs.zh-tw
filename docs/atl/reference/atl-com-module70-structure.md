---
title: "_ATL_COM_MODULE70 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
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
ms.openlocfilehash: 503c2a29cf0e70020b012911c51b056f00562374
ms.lasthandoff: 02/24/2017

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
  
## <a name="members"></a>Members  
 `cbSize`  
 使用版本控制的結構大小。  
  
 `m_hInstTypeLib`  
 此模組的類型程式庫到控制代碼執行個體。  
  
 **m_ppAutoObjMapFirst**  
 指出此模組的物件對應項目開頭的陣列元素的位址。  
  
 **m_ppAutoObjMapLast**  
 指出此模組的物件對應項目結尾的陣列元素的位址。  
  
 `m_csObjMap`  
 序列化物件的對應項目來存取重要區段。 在內部使用 ATL  
  
## <a name="remarks"></a>備註  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)定義為 typedef 的`_ATL_COM_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)






