---
title: "is_placeholder 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e50b427abcdaf8388ae35a0fef448603698e220a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="isplaceholder-class"></a>is_placeholder 類別
測試類型是否是預留位置。  
  
## <a name="syntax"></a>語法  
  
struct is_placeholder {  
   static const int value;  
   };  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 不是預留位置，常數值 `value` 就會是 0；否則其值會是它所繫結之函式呼叫引數的位置。 您可以使用它來判斷第 N 個預留位置 `_N` 的值 `N`。  
  
## <a name="example"></a>範例  
  
```cpp  
// std__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}  
```  
  
```Output  
0  
3  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [_1 Object](../standard-library/1-object.md)


