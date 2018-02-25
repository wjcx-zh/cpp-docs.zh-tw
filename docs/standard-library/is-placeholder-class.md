---
title: "is_placeholder 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5491f0a8c5ef0c6999680beb8b82cd6280f87af1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [_1 Object](../standard-library/1-object.md)

