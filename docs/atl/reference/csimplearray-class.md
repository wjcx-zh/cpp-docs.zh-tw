---
title: "CSimpleArray Class | Microsoft Docs"
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
  - "ATL.CSimpleArray"
  - "ATL::CSimpleArray"
  - "CSimpleArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArray class"
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供管理簡單陣列的方法。  
  
## 語法  
  
```  
  
      template <  
   class T,  
   class TEqual = CSimpleArrayEqualHelper< T >  
>   
class CSimpleArray  
```  
  
#### 參數  
 `T`  
 儲存的資料型別陣列。  
  
 `TEqual`  
 簽章物件，定義型別 `T`之項目的相等測試。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleArray::CSimpleArray](../Topic/CSimpleArray::CSimpleArray.md)|簡單陣列的建構函式。|  
|[CSimpleArray::~CSimpleArray](../Topic/CSimpleArray::~CSimpleArray.md)|簡單陣列的解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleArray::Add](../Topic/CSimpleArray::Add.md)|將新的項目加入至陣列。|  
|[CSimpleArray::Find](../Topic/CSimpleArray::Find.md)|尋找在陣列的項目。|  
|[CSimpleArray::GetData](../Topic/CSimpleArray::GetData.md)|傳回指向儲存在陣列中儲存的資料。|  
|[CSimpleArray::GetSize](../Topic/CSimpleArray::GetSize.md)|傳回陣列中儲存的項目數目。|  
|[CSimpleArray::Remove](../Topic/CSimpleArray::Remove.md)|從陣列中移除特定的項目。|  
|[CSimpleArray::RemoveAll](../Topic/CSimpleArray::RemoveAll.md)|從陣列中移除所有項目。|  
|[CSimpleArray::RemoveAt](../Topic/CSimpleArray::RemoveAt.md)|從陣列中移除指定的項目。|  
|[CSimpleArray::SetAtIndex](../Topic/CSimpleArray::SetAtIndex.md)|設定陣列中的指定項目。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleArray::operator](../Topic/CSimpleArray::operator.md)|從陣列中擷取項目。|  
|[CSimpleArray::operator \=](../Topic/CSimpleArray::operator%20=.md)|指派運算子。|  
  
## 備註  
 `CSimpleArray` 用來建立及管理簡單陣列提供方法，任何指定之型別的 `T`。  
  
 參數 `TEqual` 提供型別定義相等函式的方式 `T`的兩個項目。  透過建立類別類似 [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，變更相等測試的行為任何指定陣列中的是有可能的。  例如，在中，在處理指標陣列，根據值時定義相等是很有用的指標參考。  預設實作會將 **operator\=\(\)**。  
  
 `CSimpleArray` 和 [CSimpleMap](../../atl/reference/csimplemap-class.md) 用於小量項目設計。  [CAtlArray](../../atl/reference/catlarray-class.md) 和 [CAtlMap](../../atl/reference/catlmap-class.md) ，當陣列包含大量項目時，應該使用。  
  
## 需求  
 **Header:** atlsimpcoll.h  
  
## 範例  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/CPP/csimplearray-class_1.cpp)]  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)