---
title: _com_ptr_t::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8b9eac88c9387c6aeedd140159bb24482c829dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Microsoft 特定的**  
  
 封裝這個智慧型指標類型的一般介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `pInterface`  
 原始的介面指標。  
  
 `fAddRef`  
 如果是**true**，然後`AddRef`呼叫。 如果是**false**、`_com_ptr_t`物件會取得一般介面指標，而不需呼叫的擁有權`AddRef`。  
  
## <a name="remarks"></a>備註  
  
-   **附加 (**`pInterface`**)** `AddRef`則不會呼叫。 介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。  
  
-   **附加 (** `pInterface` **，**`fAddRef`**)**如果`fAddRef`是**true**，`AddRef`呼叫以遞增的參考封裝的介面指標的計數。 如果`fAddRef`是**false**，這個`_com_ptr_t`物件會取得一般介面指標，而不需呼叫的擁有權`AddRef`。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)