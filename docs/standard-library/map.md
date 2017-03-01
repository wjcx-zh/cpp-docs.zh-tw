---
title: '&lt;map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<map>
- std.<map>
- <map>
dev_langs:
- C++
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: fad398e9f18c2f45de7e071be464e3eff2e9243e
ms.lasthandoff: 02/24/2017

---
# <a name="ltmapgt"></a>&lt;map&gt;
定義容器樣板類別對應和多重對應，以及其支援的樣板。  
  
## <a name="syntax"></a>語法  
  
```  
#include <map>  
  
```  
  
## <a name="members"></a>Members  
  
### <a name="operators"></a>運算子  
  
|對應版本|多重對應版本|說明|  
|-----------------|----------------------|-----------------|  
|[operator!= (map)](../standard-library/map-operators.md#operator_neq)|[operator!= (multimap)](../standard-library/map-operators.md#operator_neq)|測試運算子左邊的對應或多重對應物件是否不等於右邊的對應或多重對應物件。|  
|[operator< (map)](../standard-library/map-operators.md#operator_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#operator_eq_eq)|測試運算子左邊的對應或多重對應物件是否小於右邊的對應或多重對應物件。|  
|[operator<= (map)](../standard-library/map-operators.md#operator_lt_)|[operator\<= (multimap)](../standard-library/map-operators.md#operator_lt_)|測試運算子左邊的對應或多重對應物件是否小於或等於右邊的對應或多重對應物件。|  
|[operator== (map)](../standard-library/map-operators.md#operator_lt__eq)|[operator== (multimap)](../standard-library/map-operators.md#operator_lt__eq)|測試運算子左邊的對應或多重對應物件是否等於右邊的對應或多重對應物件。|  
|[operator> (map)](../standard-library/map-operators.md#operator_gt_)|[operator> (multimap)](../standard-library/map-operators.md#operator_gt_)|測試運算子左邊的對應或多重對應物件是否大於右邊的對應或多重對應物件。|  
|[operator>= (map)](../standard-library/map-operators.md#operator_gt__eq)|[operator>= (multimap)](../standard-library/map-operators.md#operator_gt__eq)|測試運算子左邊的對應或多重對應物件是否大於或等於右邊的對應或多重對應物件。|  
  
### <a name="specialized-template-functions"></a>特製化樣板函式  
  
|對應版本|多重對應版本|說明|  
|-----------------|----------------------|-----------------|  
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap)|交換兩個對應或多重對應的項目。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[value_compare 類別](../standard-library/value-compare-class-map.md)|提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。|  
|[map 類別](../standard-library/map-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的唯一索引鍵。|  
|[multimap 類別](../standard-library/multimap-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的索引鍵，而且這些索引鍵不需要具有唯一的值。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




