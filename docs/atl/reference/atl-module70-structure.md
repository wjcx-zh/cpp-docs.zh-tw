---
title: "_ATL_MODULE70 Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_MODULE70"
  - "ATL::_ATL_MODULE70"
  - "ATL._ATL_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_MODULE70 structure"
  - "ATL_MODULE70 structure"
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# _ATL_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含每個 ATL 模組所使用的資料。  
  
## 語法  
  
```  
  
      struct _ATL_MODULE70{  
   UINT cbSize;  
   LONG m_nLockCnt;  
   _ATL_TERMFUNC_ELEM* m_pTermFuncs;  
   CComCriticalSection m_csStaticDataInitAndTypeInfo;  
};  
```  
  
## Members  
 `cbSize`  
 結構的大小，使用提供版本。  
  
 `m_nLockCnt`  
 參考計數決定模組所應保持作用中。  
  
 **m\_pTermFuncs**  
 追蹤註冊呼叫的函式，當 ATL 關閉。  
  
 **m\_csStaticDataInitAndTypeInfo**  
 用來協調內部資料的存取在多執行緒的情況。  
  
## 備註  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md) 定義為 `_ATL_MODULE70`typedef。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)