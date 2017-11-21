---
title: "_bstr_t::copy |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::copy
dev_langs: C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c7a3bb2997bbec1c0e402c14985353dcf0bc768
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Microsoft 特定的**  
  
 建構已封裝 `BSTR` 的複本。  
  
## <a name="syntax"></a>語法  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### <a name="parameters"></a>參數  
 `fCopy`  
 如果**true**，**複製**傳回一份包含`BSTR`，否則為**複製**傳回實際的 BSTR。  
  
## <a name="remarks"></a>備註  
 傳回新配置已封裝 `BSTR` 物件的複本。  
  
## <a name="example"></a>範例  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)