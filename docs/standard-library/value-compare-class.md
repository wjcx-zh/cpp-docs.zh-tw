---
title: "value_compare 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: value_compare
dev_langs: C++
helpviewer_keywords: value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a340acbc50c629686f010f51ce07e397e4084154
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="valuecompare-class"></a>value_compare 類別
提供函式物件，該物件可透過比較 hash_map 項目的索引鍵值來比較項目，以判斷項目在 hash_map 中的相對順序。  
  
## <a name="syntax"></a>語法  
  
```
class value_compare
 : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
    const value_type& left,
    const value_type& right) const
 {
    return (comp(left.first, right.first));

 }
protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```  
  
## <a name="remarks"></a>備註  
 由 value_compare 提供在 hash_map 所包含全部 **value_types** 項目之間的比較準則，是透過輔助類別建構函式在個別項目之間的索引鍵比較而導出。 成員函式運算子會使用型別 `key_compare` 的物件 **comp**，該物件儲存於由 value_compare 提供的函式物件中，來比較兩個項目的排序鍵元件。  
  
 對於 hash_sets 和 hash_multisets 而言 (這些是簡單容器，其中索引鍵值和項目值相同)，value_compare 相當於 `key_compare`；但對於 hash_maps 和 hash_multimaps 則否，因為項目型別 `pair` 的值與項目的索引鍵值不同。  
  
   
  
## <a name="example"></a>範例  
 如需如何宣告和使用 value_compare 的範例，請參閱 [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) 範例。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<hash_map>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>請參閱  
 [binary_function 結構](../standard-library/binary-function-struct.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)



