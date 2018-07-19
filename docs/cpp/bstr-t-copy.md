---
title: _bstr_t::copy |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d23f204e7e8a545fbee7ab516495ed711d7984a9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942951"
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Microsoft 專屬**  
  
 建構已封裝 `BSTR` 的複本。  
  
## <a name="syntax"></a>語法  
  
```  
  
BSTR copy( bool fCopy = true ) const;  
```  
  
#### <a name="parameters"></a>參數  
 *fCopy*  
 如果為 TRUE，`copy`會傳回一份內含`BSTR`，否則為`copy`傳回實際的 BSTR。  
  
## <a name="remarks"></a>備註  
 傳回新配置已封裝 `BSTR` 物件的複本。  
  
## <a name="example"></a>範例  
  
```cpp 
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)