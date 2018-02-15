---
title: _AtlCreateWndData Structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfc663429cc7cc1fe8ff6fc917f3150d621f9f75
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData Structure
此結構包含在 ATL 中的視窗化程式碼中的類別執行個體資料  
  
## <a name="syntax"></a>語法  
  
```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```  
  
## <a name="members"></a>成員  
 **m_pThis**  
 **這**用來取得存取權的類別執行個體視窗程序中的指標。  
  
 `m_dwThreadID`  
 目前的類別執行個體的執行緒 ID。  
  
 **m_pNext**  
 下一個指標`_AtlCreateWndData`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
## <a name="see-also"></a>請參閱  
 [結構](../../atl/reference/atl-structures.md)





