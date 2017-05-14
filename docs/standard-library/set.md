---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<set>
- std::<set>
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a31b01acf239fb745cf666e3a1329ee6d92eb86e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltsetgt"></a>&lt;set&gt;
定義容器範本類別 set 和 multiset，以及其支援的範本。  
  
## <a name="syntax"></a>語法  
  
```  
#include <set>  
  
```  
  
## <a name="members"></a>Members  
  
### <a name="operators"></a>運算子  
  
|set 版本|multiset 版本|描述|  
|-----------------|----------------------|-----------------|  
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|測試運算子左邊的 set 或 multiset 物件是否不等於右邊的 set 或 multiset 物件。|  
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於右邊的 set 或 multiset 物件。|  
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否小於或等於右邊的 set 或 multiset 物件。|  
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否等於右邊的 set 或 multiset 物件。|  
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於右邊的 set 或 multiset 物件。|  
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|測試運算子左邊的 set 或 multiset 物件是否大於或等於右邊的 set 或 multiset 物件。|  
  
### <a name="specialized-template-functions"></a>特製化樣板函式  
  
|set 版本|multiset 版本|說明|  
|-----------------|----------------------|-----------------|  
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|交換兩個 set 或 multiset 的項目。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[set 類別](../standard-library/set-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|  
|[multiset 類別](../standard-library/multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的項目值不須是唯一的，而且這些項目值做為索引鍵值，據此自動排序資料。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




