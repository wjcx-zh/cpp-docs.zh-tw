---
title: "const_mem_fun_t 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- const_mem_fun_t
- std.const_mem_fun_t
- xfunctional/std::const_mem_fun_t
- std::const_mem_fun_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
caps.latest.revision: 20
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
ms.openlocfilehash: d965e3b4072feb654a9920b9da9044f21d93f58b
ms.lasthandoff: 02/24/2017

---
# <a name="constmemfunt-class"></a>const_mem_fun_t 類別
配接器類別，這個類別允許不接受引數的常數成員函式在使用參考引數初始化時，可當做一元函式物件來呼叫。  
  
## <a name="syntax"></a>語法  
  
```
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>  
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
 };
```  
  
#### <a name="parameters"></a>參數  
 `Pm`  
 指標，指向要轉換成函式物件之 **Type** 類別的成員函式。  
  
 `Pleft`  
 要對其呼叫 `Pm` 成員函式的物件。  
  
## <a name="return-value"></a>傳回值  
 具適應性的一元函式。  
  
## <a name="remarks"></a>備註  
 範本類別會儲存 `Pm` 的複本，其必須為私用成員物件中 **Type** 類別的成員函式指標。 它會在傳回下列項目時定義其成員函式 `operator()`：( `Pleft`->\* `Pm`)() **const**。  
  
## <a name="example"></a>範例  
 通常並不直接使用 `const_mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun_function)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




