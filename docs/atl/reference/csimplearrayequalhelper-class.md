---
title: "CSimpleArrayEqualHelper Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSimpleArrayEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleArrayEqualHelper class"
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleArrayEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 [CSimpleArray](../../atl/reference/csimplearray-class.md) 類別的 Helper。  
  
## 語法  
  
```  
  
      template <  
   class T   
>  
class CSimpleArrayEqualHelper  
```  
  
#### 參數  
 `T`  
 一個衍生類別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleArrayEqualHelper::IsEqual](../Topic/CSimpleArrayEqualHelper::IsEqual.md)|\(靜態\) 測試相等的兩個 `CSimpleArray` 物件項目。|  
  
## 備註  
 這個特性類別是一套對於 `CSimpleArray` 類別。  它會比較儲存在 `CSimpleArray` 物件的兩個項目的方法。  根據預設，會使用 **operator\=\(\)**，項目會比較，，不過，如果陣列包含缺少自己的等號比較運算子的複雜資料型別，您需要覆寫這個類別。  
  
## 需求  
 **Header:** atlsimpcoll.h  
  
## 請參閱  
 [CSimpleArray Class](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse Class](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)