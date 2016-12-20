---
title: "money_base 類別 | Microsoft Docs"
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
  - "locale/std::money_base"
  - "money_base"
  - "std::money_base"
  - "std.money_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_base 類別"
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# money_base 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別會描述列舉型別和結構共用對樣板類別 [moneypunct](../standard-library/moneypunct-class.md)的所有特製化。  
  
## 語法  
  
```  
struct money_base : public locale::facet  
{  
    enum  
    {  
        symbol = '$',  
        sign = '+',  
        space = ' ',  
        value = 'v',  
        none = 'x'  
    };  
    typedef int part;  
    struct pattern  
    {  
        char field[_PATTERN_FIELD_SIZE];  
    };  
    money_base(  
        size_t _Refs = 0  
    );  
    ~money_base();  
};  
```  
  
## 備註  
 列舉 **part** 陣列中欄位的項目描述可能值結構樣式的。  **part** 的值為:  
  
-   比對零或更多空間的**none** 或產生。  
  
-   符合或產生一個正號或負號的**sign** 。  
  
-   比對零或更多空間的**space** 或產生空間。  
  
-   符合或產生貨幣符號的**symbol** 。  
  
-   符合或產生一個貨幣值的**value** 。  
  
## 需求  
 **Header:** \<地區設定\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)