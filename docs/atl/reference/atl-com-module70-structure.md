---
title: "_ATL_COM_MODULE70 Structure | Microsoft Docs"
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
  - "ATL::_ATL_COM_MODULE70"
  - "ATL._ATL_COM_MODULE70"
  - "_ATL_COM_MODULE70"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ATL_COM_MODULE70 structure"
  - "ATL_COM_MODULE70 structure"
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 15
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _ATL_COM_MODULE70 Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用由 COM 相關程式碼在 ATL。  
  
## 語法  
  
```  
  
      struct _ATL_COM_MODULE70{  
   UINT cbSize;  
   HINSTANCE m_hInstTypeLib;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;  
   _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;  
   CRITICAL_SECTION m_csObjMap;  
};  
```  
  
## Members  
 `cbSize`  
 結構的大小，使用提供版本。  
  
 `m_hInstTypeLib`  
 對型別程式庫的控制代碼這個模組的執行個體。  
  
 **m\_ppAutoObjMapFirst**  
 指示物件對應項目開頭的這個模組的陣列元素的位址。  
  
 **m\_ppAutoObjMapLast**  
 指示物件對應項目的結束這個模組的陣列元素的位址。  
  
 `m_csObjMap`  
 序列化物件對應項目的關鍵區段。  在內部使用 ATL。  
  
## 備註  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md) 定義為 `_ATL_COM_MODULE70`typedef。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)