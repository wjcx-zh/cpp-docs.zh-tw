---
title: '_bstr_t:: operator = |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5537f4ad3abbac9686272e15d06bfa5df0bfca6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Microsoft 特定的**  
  
 將新值指派給現有的 `_bstr_t` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### <a name="parameters"></a>參數  
 *S1*  
 `_bstr_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 *S2*  
 多位元組字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `s3`  
 Unicode 字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `var`  
 `_variant_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 **結束 Microsoft 特定的**  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例`operator=`。  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)