---
title: vector&lt;bool&gt;::reference::flip | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector<bool>::reference::flip
- std::vector<bool>::reference::flip
dev_langs:
- C++
helpviewer_keywords:
- reference::flip method
ms.assetid: ef940365-cbe4-4a87-a3e2-1f3cfa357e29
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
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 3df75ecbe47a1e6da00aa1b7a6bf55982a307d2d
ms.lasthandoff: 02/24/2017

---
# <a name="vectorltboolgtreferenceflip"></a>vector&lt;bool&gt;::reference::flip
反轉所參考 [vector\<bool>](../standard-library/vector-bool-class.md) 項目的布林值。  
  
## <a name="syntax"></a>語法  
  
```  
void flip();
```  
  
## <a name="example"></a>範例  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
## <a name="output"></a>輸出  
  
```  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<vector>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [vector\<bool>::reference 類別](../standard-library/vector-bool-reference-class.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


