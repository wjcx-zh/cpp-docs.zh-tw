---
title: _ATL_BASE_MODULE70 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 484fc4a68d0421cb12e901b2d56f30e95f6cb79b
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
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
  
## <a name="members"></a>成員  
 `cbSize`  
 用來進行版本控制的結構大小。  
  
 `m_hInst`  
 **HInstance**針對此模組 （exe 或 dll）。  
  
 `m_hInstResource`  
 預設執行個體資源控制代碼。  
  
 **m_bNT5orWin98**  
 作業系統版本資訊。 供內部使用 atl。  
  
 **dwAtlBuildVer**  
 儲存 ATL 版本 目前 0x0700。  
  
 **pguidVer**  
 ATL 的內部的 GUID。  
  
 **m_csResource**  
 用來同步處理存取具備**m_rgResourceInstance**陣列。 供內部使用 atl。  
  
 **m_rgResourceInstance**  
 用來搜尋資源的 ATL 會感知的所有資源執行個體中的陣列。 供內部使用 atl。  
  
## <a name="remarks"></a>備註  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)定義為 typedef 的`_ATL_BASE_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../../atl/reference/atl-classes.md)





