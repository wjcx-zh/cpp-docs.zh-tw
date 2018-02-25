---
title: "ctype_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- locale/std::ctype_base
dev_langs:
- C++
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45d56677e4e618fbf683000eff8d13a6a1fb6bc8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
 您可以搭配使用 OR 與這些常數來描述分類的組合。 特別是，它會一律是 true，**與 alnum** = = ( **alpha** &#124;**位數**\)和**圖形** \= \= \( **與 alnum** &#124;**符號**)。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



