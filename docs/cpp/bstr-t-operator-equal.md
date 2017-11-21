---
title: "_bstr_t:: operator = |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::operator=
dev_langs: C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5005dd0aa020ee38e4a6d29237f6ec683219ce9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
 *s1*  
 `_bstr_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 *s2*  
 多位元組字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `s3`  
 Unicode 字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `var`  
 `_variant_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 **END Microsoft 特定的**  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例`operator=`。  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)