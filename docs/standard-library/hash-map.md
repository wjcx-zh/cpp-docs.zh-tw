---
title: '&lt;hash_map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<hash_map>
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a1c256df1182c00c1b6045923ba9975f02c9bfa2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;
> [!NOTE]
>  此標頭已淘汰。 替代方案是 [<unordered_map>](../standard-library/unordered-map.md)。  
  
 定義容器樣板類別 hash_map 和 hash_multimap，以及其支援的樣板。  
  
 在 Visual C++ .NET 2003 中，<hash_map> 和 <hash_set> 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
## <a name="syntax"></a>語法  
  
```  
#include <hash_map>  
  
```  
  
### <a name="operators"></a>運算子  
  
|Hash_map 版本|Hash_multimap 版本|描述|  
|-----------------------|----------------------------|-----------------|  
|[operator!= (hash_map)](../standard-library/hash-map-operators.md#op_neq)|`operator!= (hash_multimap)`|測試運算子左邊的 hash_map 或 hash_multimap 物件是否不等於右邊的 hash_map 或 hash_multimap 物件。|  
|[operator== (hash_map)](../standard-library/hash-map-operators.md#op_eq_eq)|`operator== (hash_multimap)`|測試運算子左邊的 hash_map 或 hash_multimap 物件是否等於右邊的 hash_map 或 hash_multimap 物件。|  
  
### <a name="specialized-template-functions"></a>特製化樣板函式  
  
|Hash_map 版本|Hash_multimap 版本|描述|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_map)](../standard-library/hash-map-class.md#swap)|[swap (hash_multimap)](../standard-library/hash-multimap-class.md#swap)|交換兩個 hash_maps 或 hash_multimaps 的項目。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[hash_compare 類別](../standard-library/hash-compare-class.md)|描述一個物件，該物件可由任一雜湊相關聯的容器 (hash_map、hash_multimap、hash_set 或 hash_multiset) 當成預設 **Traits** 參數物件使用，以便排序與雜湊處理所包含的項目。|  
|[value_compare 類別](../standard-library/value-compare-class.md)|提供函式物件，該物件可透過比較 hash_map 項目的索引鍵值來比較項目，以判斷項目在 hash_map 中的相對順序。|  
|[hash_map 類別](../standard-library/hash-map-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 (其值唯一) 和相關聯資料值的配對。|  
|[hash_multimap 類別](../standard-library/hash-multimap-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 (其值可重複) 和相關聯資料值的配對。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<hash_map>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




