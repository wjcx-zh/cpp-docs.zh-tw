---
title: "_bstr_t:: operator + =，+ |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0ba8936df56359523a76992866642521f899af69
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
 *s1*  
 `_bstr_t` 物件。  
  
 *s2*  
 多位元組字串。  
  
 `s3`  
 Unicode 字串。  
  
## <a name="remarks"></a>備註  
 這些運算子會執行字串串連：  
  
-   **運算子 + = (***s1***)**將附加至封裝中的字元`BSTR`的*s1*到這個物件封裝結尾`BSTR`.      
  
-   **operator + (***s1***)**傳回新`_bstr_t`，藉由串連此物件的正確`BSTR`與*s1*。      
  
-   **operator + (***s2***&#124;***s1***)**傳回新`_bstr_t`，藉由串連的多位元組字串構成*s2*，轉換成 Unicode，與`BSTR`封裝在*s1*。          
  
-   **operator + (** `s3` **，***s1***)**傳回新`_bstr_t`Unicode 字串的串連，形成`s3`與`BSTR`封裝在*s1*。        
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)
