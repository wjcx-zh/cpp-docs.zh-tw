---
title: _bstr_t::GetAddress |Microsoft Docs
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
ms.openlocfilehash: 680588a4c045c20001b46b35c67d28e366afc52d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572037"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft 專屬**  
  
 釋放任何現有字串並傳回新配置字串的位址。  
  
## <a name="syntax"></a>語法  
  
```  
BSTR* GetAddress( );  
```  
  
## <a name="return-value"></a>傳回值  
 由 `BSTR` 包裝的 `_bstr_t` 指標。  
  
## <a name="remarks"></a>備註  
 **GetAddress**會影響所有`_bstr_t`物件共用`BSTR`。 多個`_bstr_t`態度`BSTR`透過複製建構函式使用並**運算子 =**。  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)範例使用**GetAddress**。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)