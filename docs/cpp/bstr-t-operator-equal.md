---
title: '_bstr_t:: operator = |Microsoft Docs'
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
ms.openlocfilehash: 3dfed780e0769e342ff368af453fc70764a372f0
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404469"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Microsoft 專屬**  
  
 將新值指派給現有的 `_bstr_t` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
_bstr_t& operator=(const _bstr_t& s1) throw ( );  
_bstr_t& operator=(const char* s2);  
_bstr_t& operator=(const wchar_t* s3);  
_bstr_t& operator=(const _variant_t& var);  
```  
  
#### <a name="parameters"></a>參數  
 *s1*  
 `_bstr_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 *s2*  
 多位元組字串，將被指派給現有的 `_bstr_t` 物件。  
  
 *s3*  
 Unicode 字串，將被指派給現有的 `_bstr_t` 物件。  
  
 *var*  
 `_variant_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 **結束 Microsoft 專屬**  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)如需使用的範例**運算子 =**。  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)