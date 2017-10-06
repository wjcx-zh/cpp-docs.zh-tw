---
title: "_com_ptr_t::Attach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: aa14a5fb0e54971e19de1b46317d768e7fc06a2e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
  
-   **附加 (**`pInterface`**)** `AddRef`則不會呼叫。     介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。  
  
-   **附加 (** `pInterface` **，**`fAddRef`**)**如果`fAddRef`是**true**，`AddRef`呼叫以遞增的參考封裝的介面指標的計數。       如果`fAddRef`是**false**，這個`_com_ptr_t`物件會取得一般介面指標，而不需呼叫的擁有權`AddRef`。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
