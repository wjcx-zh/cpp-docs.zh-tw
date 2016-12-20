---
title: "IAtlStringMgr Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAtlStringMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlStringMgr class"
  - "記憶體, 管理"
  - "shared classes, IAtlStringMgr"
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: 16
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAtlStringMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示介面給 `CStringT` 記憶體管理員。  
  
## 語法  
  
```  
  
__interface IAtlStringMgr  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[配置](../Topic/IAtlStringMgr::Allocate.md)|呼叫這個方法會配置新的字串資料結構。|  
|[複製](../Topic/IAtlStringMgr::Clone.md)|呼叫這個方法會傳回指標給新字串的處理常式會使用 `CSimpleStringT`另一個執行個體的使用。|  
|[Free](../Topic/IAtlStringMgr::Free.md)|呼叫這個方法會將字串資料結構。|  
|[GetNilString](../Topic/IAtlStringMgr::GetNilString.md)|傳回指向空字串物件所使用的 `CStringData` 物件。|  
|[重新配置](../Topic/IAtlStringMgr::Reallocate.md)|呼叫這個方法會重新指派字串資料結構。|  
  
## 備註  
 這個介面會處理 MFC 獨立資料類別所使用的記憶體，例如 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)、 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)和 [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。  
  
 您也可以使用這個類別會實作自己的自訂字串類別的自訂記憶體管理員。  如需詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## 需求  
 **Header:** atlsimpstr.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)