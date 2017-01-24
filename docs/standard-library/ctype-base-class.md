---
title: "ctype_base 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "locale/std::ctype_base"
  - "std.ctype_base"
  - "ctype_base"
  - "std::ctype_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype_base 類別"
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別可做為類別的基底類別 \(Base Class\) 範本 Facet 把 [ctype](../standard-library/ctype-class.md)。  用來定義用來列舉型別分類或測試字元個別或在整個範圍內的 ctype 類別的基底類別。  
  
## 語法  
  
```  
struct ctype_base : public locale::facet  
{  
    enum  
    {  
        alnum, alpha, cntrl, digit, graph,  
        lower, print, punct, space, upper,  
        xdigit  
    };  
    typedef short mask;  
    ctype_base(  
        size_t _Refs = 0  
    );  
    ~ctype_base();  
};  
```  
  
## 備註  
 它會定義列舉遮罩。  每個列舉常數 Draw 一種字元分類定義，以在標題 \<宣告的相同名稱的函式 ctype.h。\>  常數是:  
  
-   **space** 函式 \( [isspace](../Topic/isspace.md)\)  
  
-   **print** 函式 \( [isprint](../Topic/isprint.md)\)  
  
-   **cntrl** 函式 \( [iscntrl](../Topic/iscntrl.md)\)  
  
-   **upper** 函式 \( [isupper](../Topic/isupper.md)\)  
  
-   **lower** 函式 \( [islower](../Topic/islower.md)\)  
  
-   **digit** 函式 \( [isdigit](../Topic/isdigit.md)\)  
  
-   **punct** 函式 \( [ispunct](../Topic/ispunct.md)\)  
  
-   **xdigit** 函式 \( [isxdigit](../Topic/isxdigit.md)\)  
  
-   **alpha** 函式 \( [isalpha](../Topic/isalpha.md)\)  
  
-   **alnum** 函式 \( [isalnum](../Topic/isalnum.md)\)  
  
-   **graph** 函式 \( [isgraph](../Topic/isgraph.md)\)  
  
 您可以由 O 環境 Draw 分類的組合這些常數。  特別是，永遠為 true **alnum** \=\= \(**alpha** ``&#124; **digit**和 **graph** \) \=\= \(**alnum**``&#124; **punct**\)。  
  
## 需求  
 **Header:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)