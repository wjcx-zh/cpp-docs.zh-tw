---
title: "mem_fun_t 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mem_fun_t
- xfunctional/std::mem_fun_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
caps.latest.revision: 19
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 88b79a99f04dc247fe52c7b65e6a9fd5f7cd4c2f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/19/2017

---
# <a name="memfunt-class"></a>mem_fun_t 類別
配接器類別，可允許將不接受任何引數的 **non_const** 成員函式在以指標引數初始化時，當作一元函式物件來呼叫。  
  
## <a name="syntax"></a>語法  
  
```
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;

 };
```  
  
#### <a name="parameters"></a>參數  
 `_Pm`  
 指標，指向要轉換成函式物件之 **Type** 類別的成員函式。  
  
 `_Pleft`  
 要對其呼叫 `_Pm` 成員函式的物件。  
  
## <a name="return-value"></a>傳回值  
 具適應性的一元函式。  
  
## <a name="remarks"></a>備註  
 此範本類別會在私用成員物件中儲存一份 `_Pm` 的複本，這必須是 **Type** 類別之成員函式的指標。 它會將其成員函式 `operator()` 定義為傳回 ( `_Pleft`->* `_Pm`)( )。  
  
## <a name="example"></a>範例  
 通常並不直接使用 `mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [\<functional>](../standard-library/functional.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




