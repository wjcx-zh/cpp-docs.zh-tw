---
title: "const_mem_fun1_t 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 187d564f83e63f712ad2aed88679607c212deafe
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 類別
配接器類別，這個類別可在使用指標引數初始化 **const** 成員函式 (其接受單一引數) 時，將其當作二元函式物件來呼叫。  
  
## <a name="syntax"></a>語法  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>  
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>參數  
 `_Pm`  
 要轉換成函式物件之 **Type** 類別的成員函式指標。  
  
 `_Pleft`  
 要呼叫 `_Pm` 成員函式的 **Const** 物件。  
  
 `right`  
 提供給 `_Pm` 的引數。  
  
## <a name="return-value"></a>傳回值  
 具適應性的二元函式。  
  
## <a name="remarks"></a>備註  
 此範本類別會在私用成員物件中儲存一份 `_Pm` 的複本，這必須是 **Type** 類別之成員函式的指標。 它會定義其成員函式`operator()`為傳回 ( **_Pleft** -> \* * Pm) (***右邊**) **const**。  
  
## <a name="example"></a>範例  
 通常並不直接使用 `const_mem_fun1_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)



