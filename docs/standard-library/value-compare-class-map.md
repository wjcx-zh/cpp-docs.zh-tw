---
title: "value_compare 類別 (&lt;map&gt;) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
caps.latest.revision: 21
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
ms.openlocfilehash: c46338445598ef77e6b8a4c1c261962fe9e7ff0f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="valuecompare-class-ltmapgt"></a>value_compare 類別 (&lt;map&gt;)
提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。  
  
## <a name="syntax"></a>語法  
  
```
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```  
  
## <a name="remarks"></a>備註  
 由 `value_compare` 提供在對應所包含全部 **value_types** 項目之間的比較準則，是透過輔助類別建構函式在個別項目之間的索引鍵比較而導出。 成員函式運算子會使用型別 `key_compare` 的物件 **comp**，該物件儲存於由 `value_compare` 提供的函式物件中，來比較兩個項目的排序鍵元件。  
  
 對於集和多重集而言 (這些是簡單容器，其中索引鍵值和項目值相同)，`value_compare` 相當於 `key_compare`；但對於對應和多重對應則否，因為項目型別 `pair` 的值與項目的索引鍵值不同。  
  
## <a name="example"></a>範例  
  如需如何宣告和使用 [ 的範例，請參閱 ](../standard-library/map-class.md#value_comp)value_comp`value_compare` 範例。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<map>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [binary_function 結構](../standard-library/binary-function-struct.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




