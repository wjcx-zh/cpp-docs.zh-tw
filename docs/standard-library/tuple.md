---
title: "&lt; tuple &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<tuple>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "元組標頭 [TR1]"
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt; tuple &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義的範本 `tuple` 其執行個體會保留各種不同類型的物件。  
  
## <a name="syntax"></a>語法  
  
```  
#include <tuple>  
```  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[tuple](../standard-library/tuple-class.md)|包裝固定長度項目的序列。|  
|[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)|包裝 `tuple` 元素的類型。|  
|[tuple_size 類別](../standard-library/tuple-size-class-tuple.md)|包裝 `tuple` 項目計數。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 = =](../Topic/%3Ctuple%3E%20operators.md#operator_eq_eq)|比較 `tuple` 物件相等|  
|[運算子 ！ =](../Topic/%3Ctuple%3E%20operators.md#operator_neq)|比較 `tuple` 物件不等於|  
|[運算子 <](../Topic/%3Ctuple%3E%20operators.md#operator_lt_)|比較 `tuple` 物件小於|  
|[運算子 < =](../Topic/%3Ctuple%3E%20operators.md#operator_lt__eq)|比較 `tuple` 物件小於或等於|  
|[運算子 >](../Topic/%3Ctuple%3E%20operators.md#operator_gt_)|比較 `tuple` 大於物件|  
|[運算子 > =](../Topic/%3Ctuple%3E%20operators.md#operator_gt__eq)|比較 `tuple` 物件大於或等於|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[取得](../Topic/%3Ctuple%3E%20functions.md#get_function)|從 `tuple` 物件取得項目。|  
|[make_tuple](../Topic/%3Ctuple%3E%20functions.md#make_tuple_function)|可讓 `tuple` 從項目值。|  
|[繫結](../Topic/%3Ctuple%3E%20functions.md#tie_function)|可讓 `tuple` 從項目參考。|  
  
## <a name="see-also"></a>請參閱  
 [\< 陣列>](../standard-library/array.md)

