---
title: "allocator&lt;void&gt; 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
dev_langs:
- C++
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: 18
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
ms.openlocfilehash: d816804e15e7a02edbe07f131529bf719039459f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 類別
`void` 類型的範本類別配置器特製化，用於定義在此內容中具有意義的類型。  
  
## <a name="syntax"></a>語法  
  
```
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```  
  
## <a name="remarks"></a>備註  
 此類別明確地特製化 *void* 類型的範本類別 [allocator](../standard-library/allocator-class.md)。 其建構函式和指派運算子的行為與範本類別相同，但只會定義下列類型︰  
  
- [const_pointer](../standard-library/allocator-class.md#const_pointer)。  
  
- [pointer](../standard-library/allocator-class.md#pointer).  
  
- [value_type](../standard-library/allocator-class.md#value_type)。  
  
- [rebind](../standard-library/allocator-class.md#rebind)，一種巢狀範本類別。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




