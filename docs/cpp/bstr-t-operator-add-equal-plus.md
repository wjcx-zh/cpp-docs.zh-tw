---
title: '_bstr_t:: operator + =，+ |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e443b233e19f6cdc64d7d6021a9a9c078a4f327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=、+
**Microsoft 特定的**  
  
 將字元附加至 `_bstr_t` 物件的結尾或串連兩個字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### <a name="parameters"></a>參數  
 *S1*  
 `_bstr_t` 物件。  
  
 *S2*  
 多位元組字串。  
  
 `s3`  
 Unicode 字串。  
  
## <a name="remarks"></a>備註  
 這些運算子會執行字串串連：  
  
-   **運算子 + = (***s1***)** 將附加至封裝中的字元`BSTR`的*s1*到這個物件封裝結尾`BSTR`.      
  
-   **operator + (***s1***)** 傳回新`_bstr_t`，藉由串連此物件的正確`BSTR`與*s1*。      
  
-   **operator + (***s2***&#124;***s1***)** 傳回新`_bstr_t`，會串連起來所構成多位元組字串*s2*，轉換成 Unicode，與`BSTR`封裝在*s1*。          
  
-   **operator + (** `s3` **，***s1***)** 傳回新`_bstr_t`Unicode 字串的串連，形成`s3`與`BSTR`封裝在*s1*。        
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)