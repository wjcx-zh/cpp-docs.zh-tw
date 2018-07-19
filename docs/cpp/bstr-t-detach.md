---
title: _bstr_t::Detach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: cc8284bd-f68b-4fff-b2e6-ce8354dabf8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8b7bc86ae487843f925668bccfbfd8e67b8685
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940247"
---
# <a name="bstrtdetach"></a>_bstr_t::Detach
**Microsoft 專屬**  
  
 傳回 `BSTR` 所包裝的 `_bstr_t`，並將 `BSTR` 與 `_bstr_t` 中斷連結。  
  
## <a name="syntax"></a>語法  
  
```  
  
BSTR Detach( ) throw;  
  
```  
  
## <a name="return-value"></a>傳回值  
 `BSTR` 包裝 `_bstr_t`。  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)範例使用`Detach`。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)