---
title: "_bstr_t::GetAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d11479a93cf19b59ae6b824f76f9b00b10fff6b2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft 特定的**  
  
 釋放任何現有字串並傳回新配置字串的位址。  
  
## <a name="syntax"></a>語法  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 由 `BSTR` 包裝的 `_bstr_t` 指標。  
  
## <a name="remarks"></a>備註  
 `GetAddress` 會影響所有共用 `_bstr_t` 的 `BSTR` 物件。 一個以上的 `_bstr_t` 可以使用複製建構函式和 `BSTR` 來共用 `operator=`。  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)範例使用`GetAddress`。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)
