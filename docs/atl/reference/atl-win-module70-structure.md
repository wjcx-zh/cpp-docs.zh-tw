---
title: "_ATL_WIN_MODULE70 Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_WIN_MODULE70"
  - "ATL::_ATL_WIN_MODULE70"
  - "ATL._ATL_WIN_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_WIN_MODULE70 structure"
  - "ATL_WIN_MODULE70 structure"
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_WIN_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用由 Windowing 程式碼在 ATL。  
  
## 語法  
  
```  
  
      struct _ATL_WIN_MODULE70{  
   UNIT cbSize;  
   CRITICAL_SECTION m_csWindowCreate;  
   _AtlCreateWndData* m_pCreateWndList;  
   CSimpleArray<ATOM> m_rgWindowClassAtoms;  
};  
```  
  
## Members  
 `cbSize`  
 結構的大小，使用提供版本。  
  
 `m_csWindowCreate`  
 用於序列化至 Windows 登錄程式碼。  在內部使用 ATL。  
  
 **m\_pCreateWndList**  
 用來繫結視窗加入至物件。  在內部使用 ATL。  
  
 **m\_rgWindowClassAtoms**  
 用來追蹤視窗類別註冊，讓屬性可以適當地移除註冊時在終止。  在內部使用 ATL。  
  
## 備註  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md) 定義為 `_ATL_WIN_MODULE70`typedef。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)