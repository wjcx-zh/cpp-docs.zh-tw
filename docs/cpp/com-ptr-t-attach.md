---
title: _com_ptr_t::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c48da9a0ff3b9cadf0b7e228f3108277154e8417
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402880"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Microsoft 專屬**  
  
 封裝這個智慧型指標類型的一般介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
void Attach( Interface* pInterface ) throw( );  
void Attach( Interface* pInterface, bool fAddRef ) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *pInterface*  
 原始的介面指標。  
  
 *fAddRef*  
 如果它是 TRUE，則`AddRef`呼叫。 如果是 FALSE 時，`_com_ptr_t`物件會取得擁有權的一般介面指標，而不需呼叫`AddRef`。  
  
## <a name="remarks"></a>備註  
  
-   **附加 (***pInterface***)** `AddRef`就不會呼叫。 介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。 `Release` 呼叫以遞減先前封裝之指標的參考計數。  
  
-   **附加 (***pInterface* **，***fAddRef***)** 如果*fAddRef*為 TRUE， `AddRef`呼叫以遞增封裝的介面指標的參考計數。       如果*fAddRef*為 FALSE，這`_com_ptr_t`物件會取得擁有權的一般介面指標，而不需呼叫`AddRef`。 `Release` 呼叫以遞減先前封裝之指標的參考計數。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)