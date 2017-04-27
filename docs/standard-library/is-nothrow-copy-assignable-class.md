---
title: "is_nothrow_copy_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_nothrow_copy_assignable
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 23
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 64502f44f46280317028fc2e7092e28cfc75f343
ms.lasthandoff: 02/24/2017

---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 類別
測試類型是否具有編譯器已知不會擲回的複製指派運算子。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct is_nothrow_copy_assignable;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果可參考類型 `T` 的 `is_nothrow_assignable<T&, const T&>` 值為 true，類型述詞執行個體的值就會是 true，否則會是 false。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_nothrow_assignable 類別](../standard-library/is-nothrow-assignable-class.md)   






