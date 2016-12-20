---
title: "函式宣告和定義的過時形式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "舊式函式宣告"
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函式宣告和定義的過時形式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

舊式函式宣告和定義會使用與 ANSI C 標準建議的語法稍微不同的規則來宣告參數。  首先，舊式宣告沒有參數清單。  其次，在函式定義中會列出參數，不過未在參數清單中宣告它們的類型。  類型宣告會位於建構函式主體的複合陳述式之前。  舊式語法已經過時，不應該在新的程式碼中使用。  不過，仍然支援使用舊式語法程式碼。  下列範例說明宣告和定義的過時形式：  
  
```  
double old_style();           /* Obsolete function declaration */  
  
double alt_style( a , real )  /* Obsolete function definition */  
    double *real;   
    int a;   
{  
    return ( *real + a ) ;  
}  
```  
  
 不需要宣告傳回與 `int` 大小相同之整數或指標的函式，但仍建議宣告。  
  
 為了要符合 ANSI C 標準，使用省略符號的舊樣式函式宣告目前在使用 \/Za 選項編譯時會產生錯誤，使用 \/Ze 編譯時會產生層級 4 的警告。  例如：  
  
```  
void funct1( a, ... )  /* Generates a warning under /Ze or */  
int a;                 /* an error when compiling with /Za */  
{  
}  
```  
  
 您應該將這個宣告重新撰寫為原型：  
  
```  
void funct1( int a, ... )  
{  
}  
```  
  
 如果您後續宣告或定義了相同的函式，其中具有省略符號或其參數的類型與升級後的類型不同，則舊式函式宣告也會產生警告。  
  
 下一節 \([C 函式定義](../c-language/c-function-definitions.md)\) 中將顯示函式定義的語法，包括舊式語法。  在舊式語法中，參數清單的非終端項為 *identifier\-list*。  
  
## 請參閱  
 [函式概觀](../c-language/overview-of-functions.md)