---
title: '&lt;utility&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <utility>
- utility/std::<utility>
- std.<utility>
- std::<utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 67792e92a4a8336c025249a5d1322d00360a62c5
ms.lasthandoff: 02/24/2017

---
# <a name="ltutilitygt"></a>&lt;utility&gt;
可定義 C++ 標準程式庫類型、函式與運算子，並協助建構及管理成對的物件，當需要將兩個物件視為一體時相當實用。  
  
## <a name="syntax"></a>語法  
  
```  
#include <utility>  
  
```  
  
## <a name="remarks"></a>備註  
 C++ 標準程式庫中很廣泛地運用配對。 做為引數並傳回不同函式的值，以及做為容器的項目型別，例如 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)時，都需要用到配對。 \<map> 會自動納入 \<utility> 標頭，以協助管理其索引及成對的鍵/值型別項目。  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|包裝 `pair` 項目類型的類別。|  
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|類別，其中包裝 `pair` 項目計數。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[forward](../standard-library/utility-functions.md#forward)|保留引數的參考類型 (可能是 `lvalue` 或 `rvalue`)，避免被完整轉寄遮蔽。|  
|[get](../standard-library/utility-functions.md#get)|函式，其可從 `pair` 物件取得項目。|  
|[make_pair](../standard-library/utility-functions.md#make_pair)|範本協助程式函式，可用以建構 `pair` 類型的物件，而其中的元件類型會以傳遞為參數的資料類型做為基礎。|  
|[move](../standard-library/utility-functions.md#move)|傳回已傳入的引數，做為 `rvalue` 參考。|  
|[swap](../standard-library/utility-functions.md#swap)|交換兩個 `pair` 物件的項目。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator!=](../standard-library/utility-operators.md#operator_neq)|測試成對運算子左側的物件是否不等於右側的物件。|  
|[operator==](../standard-library/utility-operators.md#operator_eq_eq)|測試成對運算子左側的物件是否等於右側的物件。|  
|[operator<](../standard-library/utility-operators.md#operator_lt_)|測試成對運算子左側的物件是否小於右側的物件。|  
|[operator\<=](../standard-library/utility-operators.md#operator_lt__eq)|測試成對運算子左側的物件是否小於或等於右側的物件。|  
|[operator>](../standard-library/utility-operators.md#operator_gt_)|測試成對運算子左側的物件是否大於右側的物件。|  
|[operator>=](../standard-library/utility-operators.md#operator_gt__eq)|測試成寺運算子左側的物件是否大於或等於右側的物件。|  
  
### <a name="structs"></a>結構  
  
|||  
|-|-|  
|[identity](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|類型，其提供可將兩個物件視為單一物件的功能。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




