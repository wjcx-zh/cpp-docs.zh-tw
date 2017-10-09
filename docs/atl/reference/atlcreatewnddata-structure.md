---
title: "_AtlCreateWndData 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: a5b0811e88188bb29ef3153f739804cbdac66083
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData 結構
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
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)






