---
title: "const_mem_fun1_ref_t 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun1_ref_t
dev_langs: C++
helpviewer_keywords: const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95b81ca5618cabd32af90836a67f29bf9b1923b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t 類別
配接器類別，這個類別可在使用參考引數初始化 **const** 成員函式 (其接受單一引數) 時，將其作為二元函式物件來呼叫。  
  
## <a name="syntax"></a>語法  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
 : public binary_function<Type, Arg, Result> 
 {
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>參數  
 `Pm`  
 要轉換成函式物件之 **Type** 類別的成員函式指標。  
  
 `left`  
 要呼叫 `Pm` 成員函式的 **Const** 物件。  
  
 `right`  
 提供給 `Pm` 的引數。  
  
## <a name="return-value"></a>傳回值  
 具適應性的二元函式。  
  
## <a name="remarks"></a>備註  
 範本類別會儲存 `Pm` 的複本，其必須為私用成員物件中 **Type** 類別的成員函式指標。 它會在傳回下列項目時定義其成員函式 `operator()`：( `left`.\**Pm*)( `right`) **const**。  
  
## <a name="example"></a>範例  
 `const_mem_fun1_ref_t` 的建構函式通常不會直接使用，而 helper 函式 `mem_fun_ref` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)



