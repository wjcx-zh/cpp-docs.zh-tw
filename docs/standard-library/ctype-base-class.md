---
title: "ctype_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::ctype_base
- std.ctype_base
- ctype_base
- std::ctype_base
dev_langs:
- C++
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 59ec50c7e68b4d79b97218a8cd24df391198e758
ms.lasthandoff: 02/24/2017

---
# <a name="ctypebase-class"></a>ctype_base 類別
此類別可作為 [ctype](../standard-library/ctype-class.md) 範本類別 Facet 的基底類別。 ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。  
  
## <a name="syntax"></a>語法  
  
```
struct ctype_base : public locale::facet
{
    enum
 {
    alnum,
 alpha,
    cntrl,
 digit,
    graph,
 lower,
    print,
 punct,
    space,
 upper,
    xdigit
 };
    typedef short mask;
    ctype_base(
 size_t _Refs = 0);

 ~ctype_base();

};
```  
  
## <a name="remarks"></a>備註  
 此項目可定義列舉遮罩。 每個列舉常數皆描述不同字元分類方式的特性，如 \<ctype.h> 標頭中宣告之類似名稱的函式所定義。 這些常數如下：  
  
- **space** (函式 [isspace](../standard-library/locale-functions.md#isspace))  
  
- **print** (函式 [isprint](../standard-library/locale-functions.md#isprint))  
  
- **cntrl** (函式 [iscntrl](../standard-library/locale-functions.md#iscntrl))  
  
- **upper** (函式 [isupper](../standard-library/locale-functions.md#isupper))  
  
- **lower** (函式 [islower](../standard-library/locale-functions.md#islower))  
  
- **digit** (函式 [isdigit](../standard-library/locale-functions.md#isdigit))  
  
- **punct** (函式 [ispunct](../standard-library/locale-functions.md#ispunct))  
  
- **xdigit** (函式 [isxdigit](../standard-library/locale-functions.md#isxdigit))  
  
- **alpha** (函式 [isalpha](../standard-library/locale-functions.md#isalpha))  
  
- **alnum** (函式 [isalnum](../standard-library/locale-functions.md#isalnum))  
  
- **graph** (函式 [isgraph](../standard-library/locale-functions.md#isgraph))  
  
 您可以搭配使用 OR 與這些常數來描述分類的組合。 值得注意的是，**alnum** == ( **alpha**``&#124; **digit**\) and **graph** \=\= \( **alnum**``&#124; **punct**) 一定是 true。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




