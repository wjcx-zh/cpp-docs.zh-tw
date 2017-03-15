---
title: "_ATL_BASE_MODULE70 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
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
ms.sourcegitcommit: 347e7bf7cd9173fb2815f44fc052ec23ab4055a6
ms.openlocfilehash: 7456d441d7b3fb74f404f29c893c492feab10ed9
ms.lasthandoff: 02/24/2017

---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 結構
使用 ATL 任何專案使用的  
  
## <a name="syntax"></a>語法  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>Members  
 `cbSize`  
 使用版本控制的結構大小。  
  
 `m_hInst`  
 **HInstance**這個模組 （exe 或 dll）。  
  
 `m_hInstResource`  
 預設執行個體資源控制代碼。  
  
 **m_bNT5orWin98**  
 作業系統版本資訊。 在內部使用 ATL  
  
 **dwAtlBuildVer**  
 將 ATL 版本 目前 0x0700。  
  
 **pguidVer**  
 ATL 的內部的 GUID。  
  
 **m_csResource**  
 用來同步存取**m_rgResourceInstance**陣列。 在內部使用 ATL  
  
 **m_rgResourceInstance**  
 用來搜尋資源的 ATL 是知道的所有資源執行個體中的陣列。 在內部使用 ATL  
  
## <a name="remarks"></a>備註  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定義為 typedef 的`_ATL_BASE_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcore.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)






