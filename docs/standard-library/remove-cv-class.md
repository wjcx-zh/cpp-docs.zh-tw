---
title: "remove_cv 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- remove_cv
- type_traits/std::remove_cv
dev_langs:
- C++
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: e8e219b296e352fb5ad2f6e470126bfd2b773355
ms.lasthandoff: 02/24/2017

---
# <a name="removecv-class"></a>remove_cv 類別
從類型建立非 const/volatile 類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <class T>  
struct remove_cv;  
 
template <class T>  
using remove_cv_t = typename remove_cv<T>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要修改的類型。  
  
## <a name="remarks"></a>備註  
 `remove_cv<T>` 執行個體儲存修改的類型，如果 `T1` 的格式為 `T`、`const T1` 或 `volatile T1`，類型為 `const volatile T1`，否則為 `T`。  
  
## <a name="example"></a>範例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_cv_t<const volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_cv_t<const volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_cv_t<const volatile int> == int  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_const 類別](../standard-library/remove-const-class.md)   
 [remove_volatile 類別](../standard-library/remove-volatile-class.md)

