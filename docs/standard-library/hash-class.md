---
title: "hash 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
dev_langs:
- C++
helpviewer_keywords:
- hash class
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
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
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: d549fb7aeed268327122532e6c4390ac931740e7
ms.lasthandoff: 02/24/2017

---
# <a name="hash-class"></a>hash 類別
計算值的雜湊碼。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Ty>  
struct hash {  
    size_t operator()(Ty val) const; 
};  
```  
  
## <a name="remarks"></a>備註  
函式物件會定義雜湊函式，適用於將 *Ty* 類型的值對應到索引值的分佈。 成員 `operator()` 會傳回 *val* 的雜湊碼，適合用來與範本類別 `unordered_map`、`unordered_multimap`、`unordered_set` 及 `unordered_multiset` 搭配使用。 標準程式庫提供適用於基本類型的特製化：*Ty* 可以是任何純量類型，包括指標類型和列舉類型。 此外，還有適用於程式庫類型 `string`、`wstring`、`u16string`、`u32string`、`string_view`、`wstring_view`、`u16string_view`、`u32string_view`、`bitset`、`error_code`、`error_condition`、`optional`、`shared_ptr`、`thread`、`type_index`、`unique_ptr`、`variant` 及 `vector<bool>` 的特製化。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
3  
```  
  
## <a name="requirements"></a>需求  
**標頭：**\<functional>  
  
**命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<unordered_map>](../standard-library/unordered-map.md)   
 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)   
 [unordered_multiset 類別](../standard-library/unordered-multiset-class.md)   
 [<unordered_set>](../standard-library/unordered-set.md)


