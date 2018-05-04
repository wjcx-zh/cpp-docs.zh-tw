---
title: _ATL_COM_MODULE70 結構 |Microsoft 文件
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
ms.openlocfilehash: 06c0fa2af67ddd649783c9e062a1b93b87dd0b39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 結構
使用 COM 相關 ATL 中的程式碼  
  
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
 `cbSize`  
 用來進行版本控制的結構大小。  
  
 `m_hInstTypeLib`  
 類型程式庫，針對此模組控制代碼的執行個體。  
  
 **m_ppAutoObjMapFirst**  
 指出此模組的物件對應項目開頭的陣列元素的位址。  
  
 **m_ppAutoObjMapLast**  
 指出此模組的物件對應項目結尾的陣列元素的位址。  
  
 `m_csObjMap`  
 序列化物件的對應項目存取的重要區段。 供內部使用 atl。  
  
## <a name="remarks"></a>備註  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)定義為 typedef 的`_ATL_COM_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)





