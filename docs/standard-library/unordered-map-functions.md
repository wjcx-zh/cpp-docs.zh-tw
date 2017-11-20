---
title: "&lt;unordered_map&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_map/std::swap
- unordered_map/std::swap (unordered_map)
- unordered_map/std::swap (unordered_multimap)
dev_langs:
- C++
ms.assetid: cf2e4115-f205-4a0e-90be-a143ffcc1f44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::swap (unordered_map/multimap)
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: ae6173e491fe4620734d1204a7d2e109be9367d7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltunorderedmapgt-functions"></a>&lt;unordered_map&gt; 函式
|||  
|-|-|  
|[swap (unordered_map)](#swap)|[swap (unordered_multimap)](#swap_function_multimap)|  
  
##  <a name="swap"></a>  swap (unordered_map)  
 交換兩個容器的內容。  
  
```  
template <class Key, class Ty, class Hash, class Pred, class Alloc>  
void swap(
    unordered_map <Key, Ty, Hash, Pred, Alloc>& left,  
    unordered_map <Key, Ty, Hash, Pred, Alloc>& right);
```  
  
### <a name="parameters"></a>參數  
 `Key`  
 索引鍵類型。  
  
 `Ty`  
 對應的類型。  
  
 `Hash`  
 雜湊函式物件類型。  
  
 `Pred`  
 相等比較函式物件類型。  
  
 `Alloc`  
 配置器類別。  
  
 `left`  
 要交換的第一個容器。  
  
 `right`  
 要交換的第二個容器。  
  
### <a name="remarks"></a>備註  
 範本函式執行 `left.`[unordered_map::swap](../standard-library/unordered-map-class.md#swap)`(right)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__u_m_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    Mymap c2;   
  
    c2.insert(Mymap::value_type('d', 4));   
    c2.insert(Mymap::value_type('e', 5));   
    c2.insert(Mymap::value_type('f', 6));   
  
    c1.swap(c2);   
  
// display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="swap_function_multimap"></a>  swap (unordered_multimap)  
 交換兩個容器的內容。  
  
```  
template <class Key, class Ty, class Hash, class Pred, class Alloc>  
void swap(
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& left,  
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& right);
```  
  
### <a name="parameters"></a>參數  
 `Key`  
 索引鍵類型。  
  
 `Ty`  
 對應的類型。  
  
 `Hash`  
 雜湊函式物件類型。  
  
 `Pred`  
 相等比較函式物件類型。  
  
 `Alloc`  
 配置器類別。  
  
 `left`  
 要交換的第一個容器。  
  
 `right`  
 要交換的第二個容器。  
  
### <a name="remarks"></a>備註  
 範本函式執行 `left.`[unordered_multimap::swap](../standard-library/unordered-multimap-class.md#swap)`(right)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__u_mm_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

    // display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
## <a name="see-also"></a>另請參閱  
 [<unordered_map>](../standard-library/unordered-map.md)

