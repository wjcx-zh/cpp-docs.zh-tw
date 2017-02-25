---
title: "_pctype、_pwctype、_wctype、_mbctype、_mbcasemap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pwctype"
  - "pctype"
  - "mbctype"
  - "mbcasemap"
  - "_mbcasemap"
  - "_mbctype"
  - "_pctype"
  - "_wctype"
  - "_pcwtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wctype 函式"
  - "_pwctype 函式"
  - "_pctype 函式"
  - "_mbctype 函式"
  - "wctype 函式"
  - "pwctype 函式"
  - "pctype 函式"
  - "mbcasemap 函式"
  - "mbctype 函式"
  - "_mbcasemap 函式"
ms.assetid: 7f5e1107-c43b-4b9b-b387-781e6d2373cb
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _pctype、_pwctype、_wctype、_mbctype、_mbcasemap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些全域變數字元類別使用的相關資訊運作。  它們僅供內部使用。  
  
## 語法  
  
```  
extern const unsigned short *_pctype;  
extern const wctype_t *_pwctype;  
extern const unsigned short _wctype[];  
extern unsigned char _mbctype[];  
extern unsigned char _mbcasemap[];  
```  
  
## 備註  
 `_pwctype`和 `_wctype` 函式在內部使用 `_pctype`中的資訊 [isupper、\_isupper\_l、iswupper、\_iswupper\_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)、 [islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)、 [isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)、 [isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)、 [isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)、 [isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)、 [ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)、 [isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)和 [iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)，以及 [toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md) 和 [tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md) 函式。  應該使用這些函式而不是存取這些全域變數。  
  
 `_mbcasemap`和 [\_ismbbkalnum、\_ismbbkalnum\_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md) 函式在內部使用 `_mbctype`中的資訊 [\_ismbbkana、\_ismbbkana\_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)、 [\_ismbbkpunct、\_ismbbkpunct\_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)、 [\_ismbbkprint、\_ismbbkprint\_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)、 [\_ismbbalpha](http://msdn.microsoft.com/zh-tw/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0)、 [\_ismbbpunct、\_ismbbpunct\_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)、 [\_ismbbalnum、\_ismbbalnum\_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)、 [\_ismbbprint、\_ismbbprint\_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)、 [\_ismbbgraph、\_ismbbgraph\_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)和 [\_ismbblead、\_ismbblead\_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)，以及 [\_ismbbtrail、\_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 和 [\_ismbslead、\_ismbstrail、\_ismbslead\_l、\_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md) 以及 [\_ismbslead、\_ismbstrail、\_ismbslead\_l、\_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md) 函式。  使用這些函式而不是存取全域變數。  
  
## 需求  
 不會公開使用。  
  
## 請參閱  
 [is、isw 常式](../c-runtime-library/is-isw-routines.md)   
 [\_\_pctype\_func](../c-runtime-library/pctype-func.md)