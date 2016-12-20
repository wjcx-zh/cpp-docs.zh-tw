---
title: "傳回類型 | Microsoft Docs"
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
  - "資料類型 [C++], 函式傳回類型"
  - "函式傳回類型"
  - "函式傳回類型, 語法"
  - "函式 [C++], 傳回類型"
  - "return 關鍵字 [C++], 函式傳回類型"
  - "傳回值 [C++]"
  - "傳回值 [C++], Function 程序"
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 傳回類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函式的傳回類型會建立函式傳回值的大小和類型，並且對應於下列語法中的類型規範：  
  
## 語法  
 *function\-definition*：  
 *declaration\-specifiers*  opt *attribute\-seq* opt *declarator declaration\-list* opt *compound\-statement*  
  
 \/\* *attribute\-seq* 是 Microsoft 專有 \*\/  
  
 *declaration\-specifiers*：  
 *storage\-class\-specifier declaration\-specifiers*  opt  
  
 *type\-specifier declaration\-specifiers*  opt  
  
 *type\-qualifier declaration\-specifiers*  opt  
  
 *type\-specifier*：  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **signed**  
  
 **unsigned**  
  
 *struct\-or\-union\-specifier*  
  
 *enum\-specifier*  
  
 *typedef\-name*  
  
 *type\-specifier* 可以指定任何基本、結構或等位類型。  如果您未包含 *type\-specifier*，則會假設為傳回類型 `int`。  
  
 函式定義中提供的傳回類型必須符合程式中其他位置之函式宣告中的傳回類型。  當包含運算式的 `return` 陳述式執行時，函式就會傳回值。  會求出運算式的值，於必要時轉換成傳回值類型，並且返回呼叫函式所在的點。  如果函式是使用傳回類型 `void` 宣告，則包含運算式的傳回陳述式會產生警告，而且不會求出運算式的值。  
  
 下列範例將說明函式傳回值。  
  
```  
typedef struct    
{  
    char name[20];  
    int id;  
    long class;  
} STUDENT;  
  
/* Return type is STUDENT: */  
  
STUDENT sortstu( STUDENT a, STUDENT b )  
{  
    return ( (a.id < b.id) ? a : b );  
}  
```  
  
 這個範例會定義具有 `typedef` 宣告的 `STUDENT` 類型，並且將函式 `sortstu` 定義為具有 `STUDENT` 傳回類型。  函式會選取並傳回它的兩個結構引數的其中一個。  在後續函式呼叫中，編譯器會檢查並確定引數類型為 `STUDENT`。  
  
> [!NOTE]
>  不傳遞整個結構，而是傳遞結構的指標，可提升效率。  
  
```  
char *smallstr( char s1[], char s2[] )  
{  
    int i;  
  
    i = 0;  
    while ( s1[i] != '\0' && s2[i] != '\0' )  
        i++;  
    if ( s1[i] == '\0' )  
        return ( s1 );  
    else  
        return ( s2 );  
}  
```  
  
 這個範例會定義傳回字元陣列指標的函式。  這個函式會採用兩個字元陣列 \(字串\) 做為引數，並傳回兩個字串中較短者的指標。  陣列指標會指向第一個陣列元素並擁有其類型，因此，函式的傳回類型會是 `char` 類型的指標。  
  
 您不需要在呼叫函式之前使用 `int` 傳回類型宣告函式，不過建議您使用原型，如此才能夠檢查引數和傳回值的類型是否正確。  
  
## 請參閱  
 [C 函式定義](../c-language/c-function-definitions.md)