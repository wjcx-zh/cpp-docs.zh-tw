---
title: "CSimpleMapEqualHelper Class | Microsoft Docs"
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
  - "CSimpleMapEqualHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleMapEqualHelper class"
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleMapEqualHelper Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 類別的 Helper。  
  
## 語法  
  
```  
  
      template <  
   class TKey,  
   class TVal   
>  
class CSimpleMapEqualHelper  
```  
  
#### 參數  
 `TKey`  
 關鍵項目。  
  
 `TVal`  
 值項目。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleMapEqualHelper::IsEqualKey](../Topic/CSimpleMapEqualHelper::IsEqualKey.md)|\(靜態\) 的相等測試兩個索引鍵。|  
|[CSimpleMapEqualHelper::IsEqualValue](../Topic/CSimpleMapEqualHelper::IsEqualValue.md)|\(靜態\) 的相等測試兩個值。|  
  
## 備註  
 這個特性類別是一套對於 `CSimpleMap` 類別。  它會比較兩個物件 `CSimpleMap` 項目提供方法 \(特別是，機碼和值元件\) 是否相等。  根據預設，會使用 `operator==()`，機碼和值進行比較，，不過，如果缺少對應包含自己的等號比較運算子的複雜資料型別，這個類別可覆寫提供這項必要的額外功能。  
  
## 需求  
 **標題:** atlsimpcoll.h  
  
## 請參閱  
 [CSimpleMapEqualHelperFalse Class](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)