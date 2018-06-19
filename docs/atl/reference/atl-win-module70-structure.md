---
title: _ATL_WIN_MODULE70 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 587b115c428b0d82183abbec9f712ff06ea448f4
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256076"
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
 `cbSize`  
 用來進行版本控制的結構大小。  
  
 `m_csWindowCreate`  
 用來序列化視窗註冊程式碼存取。 供內部使用 atl。  
  
 **m_pCreateWndList**  
 用來將 windows 繫結至其物件。 供內部使用 atl。  
  
 **m_rgWindowClassAtoms**  
 用來追蹤視窗類別註冊，讓它們可以適當地取消註冊，在終止。 供內部使用 atl。  
  
## <a name="remarks"></a>備註  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)定義為 typedef 的`_ATL_WIN_MODULE70`。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../../atl/reference/atl-classes.md)





