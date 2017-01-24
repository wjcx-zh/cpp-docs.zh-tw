---
title: "CSimpleMapEqualHelperFalse Class | Microsoft Docs"
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
  - "ATL::CSimpleMapEqualHelperFalse"
  - "CSimpleMapEqualHelperFalse"
  - "ATL.CSimpleMapEqualHelperFalse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelperFalse class"
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleMapEqualHelperFalse Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 類別的 Helper。  
  
## 語法  
  
```  
  
template < class TKey, class TVal > class CSimpleMapEqualHelperFalse  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](../Topic/CSimpleMapEqualHelperFalse::IsEqualKey.md)|\(靜態\) 的相等測試兩個索引鍵。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](../Topic/CSimpleMapEqualHelperFalse::IsEqualValue.md)|\(錯誤靜態\) 的傳回。|  
  
## 備註  
 這個特性類別是一套對於 `CSimpleMap` 類別。  它會比較。 `CSimpleMap` 物件包含兩個項目，尤其是兩個值項目或兩個索引鍵項目提供一個方法。  
  
 要比較的值永遠傳回 false，此外，必要時，會使用引數呼叫 `ATLASSERT` 錯誤，若是參考。  在相等測試未充分定義的情況下，這個類別允許包含索引鍵\/值組的導覽中大部分的方法都正確運作，但失敗視比較 [CSimpleMap::FindVal](../Topic/CSimpleMap::FindVal.md)之類的方法的明確定義的模式。  
  
## 需求  
 **Header:** atlsimpcoll.h  
  
## 請參閱  
 [CSimpleMapEqualHelper Class](../../atl/reference/csimplemapequalhelper-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)