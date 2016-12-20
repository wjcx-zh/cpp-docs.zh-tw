---
title: "_AtlCreateWndData Structure | Microsoft Docs"
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
  - "ATL::_AtlCreateWndData"
  - "ATL._AtlCreateWndData"
  - "_AtlCreateWndData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AtlCreateWndData structure"
  - "AtlCreateWndData structure"
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _AtlCreateWndData Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個結構包含類別執行個體資料是在 ATL 的 Windowing 程式碼。  
  
## 語法  
  
```  
  
      struct _AtlCreateWndData{  
   void* m_pThis;  
   DWORD m_dwThreadID;  
   _AtlCreateWndData* m_pNext;  
};  
```  
  
## Members  
 **m\_pThis**  
 用來 **this** 指標取得對類別執行個體上的視窗程序。  
  
 `m_dwThreadID`  
 目前類別執行個體的執行緒 ID。  
  
 **m\_pNext**  
 會將設定為下一 `_AtlCreateWndData` 物件的指標。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)