---
title: "_bstr_t::Attach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
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
ms.openlocfilehash: 0541fadf224fd3f13377111d1bb1b7f5aca2f995
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtattach"></a>_bstr_t::Attach
**Microsoft 特定的**  
  
 將 `_bstr_t` 包裝函式連結至 `BSTR`。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### <a name="parameters"></a>參數  
 *s*  
 要與 `BSTR` 變數產生關聯或指派給該變數的 `_bstr_t`。  
  
## <a name="remarks"></a>備註  
 如果 `_bstr_t` 先前已附加至另一個 `BSTR`，且其他 `_bstr_t` 變數都不會使用 `BSTR`，則 `_bstr_t` 將會清除 `BSTR` 資源。  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例**附加**。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)
