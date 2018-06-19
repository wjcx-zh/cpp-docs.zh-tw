---
title: _bstr_t::GetAddress |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88accb8b614a5a07a7abf688790a80786f465607
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409966"
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)