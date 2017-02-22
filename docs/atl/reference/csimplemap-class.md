---
title: "CSimpleMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSimpleMap"
  - "ATL.CSimpleMap"
  - "CSimpleMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMap class"
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CSimpleMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供一個簡單的對應陣列提供支援。  
  
## 語法  
  
```  
  
      template <   
   class TKey,  
   class TVal,  
   class TEqual = CSimpleMapEqualHelper< TKey, TVal >   
>   
class CSimpleMap  
```  
  
#### 參數  
 `TKey`  
 按鍵字元型別。  
  
 `TVal`  
 值項目型別。  
  
 `TEqual`  
 簽章物件，定義型別 `T`之項目的相等測試。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleMap::\_ArrayElementType](../Topic/CSimpleMap::_ArrayElementType.md)|實值型別的 Typedef。|  
|[CSimpleMap::\_ArrayKeyType](../Topic/CSimpleMap::_ArrayKeyType.md)|關鍵的型別的 Typedef。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleMap::CSimpleMap](../Topic/CSimpleMap::CSimpleMap.md)|建構函式。|  
|[CSimpleMap::~CSimpleMap](../Topic/CSimpleMap::~CSimpleMap.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleMap::Add](../Topic/CSimpleMap::Add.md)|將索引鍵和關聯的值加入至對應陣列。|  
|[CSimpleMap::FindKey](../Topic/CSimpleMap::FindKey.md)|尋找特定的索引鍵。|  
|[CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md)|尋找特定值。|  
|[CSimpleMap::GetKeyAt](../Topic/CSimpleMap::GetKeyAt.md)|擷取指定之的索引鍵。|  
|[CSimpleMap::GetSize](../Topic/CSimpleMap::GetSize.md)|傳回項目數目對應陣列中的。|  
|[CSimpleMap::GetValueAt](../Topic/CSimpleMap::GetValueAt.md)|擷取指定的值。|  
|[CSimpleMap::Lookup](../Topic/CSimpleMap::Lookup.md)|傳回值與指定索引鍵。|  
|[CSimpleMap::Remove](../Topic/CSimpleMap::Remove.md)|移除索引鍵和值。|  
|[CSimpleMap::RemoveAll](../Topic/CSimpleMap::RemoveAll.md)|移除所有索引鍵和值。|  
|[CSimpleMap::RemoveAt](../Topic/CSimpleMap::RemoveAt.md)|移除特定索引鍵和值。|  
|[CSimpleMap::ReverseLookup](../Topic/CSimpleMap::ReverseLookup.md)|傳回索引鍵與指定的值。|  
|[CSimpleMap::SetAt](../Topic/CSimpleMap::SetAt.md)|將值與指定索引鍵。|  
|[CSimpleMap::SetAtIndex](../Topic/CSimpleMap::SetAtIndex.md)|設定特定索引鍵和值。|  
  
## 備註  
 `CSimpleMap` 進行簡單的對應陣列的任何指定型別的支援 `T`，處理未按順序的主要項目和其關聯的值。  
  
 參數 `TEqual` 提供型別定義相等函式的方式 `T`的兩個項目。  透過建立類別類似 [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，變更相等測試的行為任何指定陣列中的是有可能的。  例如，在中，在處理指標陣列，根據值時定義相等是很有用的指標參考。  預設實作會將 **operator\=\=\(\)**。  
  
 `CSimpleMap` 和 [CSimpleArray](../../atl/reference/csimplearray-class.md) 只是為了提供先前的 ATL 版本，然後， [CAtlArray](../../atl/reference/catlarray-class.md) 和 [CAtlMap](../../atl/reference/catlmap-class.md)提供更完整且更有效率的 set 實作。  
  
 不同於 ATL 和 MFC 的其他對應的集合，這個類別會實作簡單的陣列，然後，搜尋要求線性搜尋。  `CAtlMap` ，當陣列包含大量項目時，應該使用。  
  
## 需求  
 **Header:** atlsimpcoll.h  
  
## 範例  
 [!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/CPP/csimplemap-class_1.cpp)]  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)