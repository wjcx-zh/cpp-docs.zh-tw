---
title: "is_nothrow_copy_assignable 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_copy_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 798bd496504dafe2f4d9ac2510fef37b5bce0b91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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




