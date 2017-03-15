---
title: "C 類型規範 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "規範, 類型"
  - "類型規範, C"
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# C 類型規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

宣告中的類型指定名稱會定義變數或函式宣告的類型。  
  
## 語法  
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
  
 **signed char**、**signed int**、**signed short int** 和 **signed long int** 類型加上與其對應的 `unsigned` 和 `enum`，稱為「整數」類型。  **float**、**double** 和 `long double` 類型指定名稱稱為「浮點」或「浮點數」類型。  您可以在變數或函式宣告中使用任何整數或浮點類型指定名稱。  如果宣告中未提供 *type\-specifier*，則會被當做 `int`。  
  
 選擇性關鍵字 **signed** 和 `unsigned` 可以在任何整數類型之前或之後 \(`enum` 除外\)，而且也可單獨做為類型指定名稱使用，在此情況下，這類關鍵字即為 **signed int** 和 `unsigned int`。  單獨使用時，會假設關鍵字 `int` 為 **signed**。  單獨使用時，關鍵字 **long** 和 **short** 即為 **long int** 和 `short int`。  
  
 列舉類型被視為基本類型。  列舉類型的類型指定名稱會在[列舉宣告](../c-language/c-enumeration-declarations.md)中討論。  
  
 關鍵字 `void` 有三個用途：指定函式傳回類型、指定不使用引數之函式的引數類型清單，以及指定未指定類型的指標。  您可以使用 `void` 類型宣告不傳回值的函式或宣告未指定類型的指標。  如需有關 `void` 單獨出現在函式名稱之後並以括號括住時的詳細資訊，請參閱[引數](../c-language/arguments.md)。  
  
 **Microsoft 特定的**  
  
 類型檢查現在符合 ANSI 標準，這表示 **short** 和 `int` 類型是不同的類型。  例如，這是在舊版編譯器中接受之 Microsoft C 編譯器的重新定義。  
  
```  
int   myfunc();  
short myfunc();  
```  
  
 下一個範例也會產生關於不同類型間接取值的警告：  
  
```  
int *pi;  
short *ps;  
  
ps = pi;  /* Now generates warning */  
```  
  
 Microsoft C 編譯器也會產生是否帶正負號之差異的警告。  例如：  
  
```  
signed int *pi;  
unsigned int *pu  
  
pi = pu;  /* Now generates warning */  
```  
  
 會評估類型 `void` 運算式的副作用。  您無法以任何方式使用具有 `void` 類型之運算式的 \(不存在的\) 值，也不能將 `void` 運算式 \(透過隱含或明確轉換\) 轉換為 `void` 以外的任何類型。  如果您在需要 `void` 運算式的內容使用任何其他類型的運算式，則會捨棄其值。  
  
 為符合 ANSI 規格，不能將 **void\*\***  做為 **int\*\*** 使用。  只有 **void\*** 能夠當做未指定類型的指標使用。  
  
 **END Microsoft 特定的**  
  
 您可以使用 `typedef` 宣告建立其他類型指定名稱，如 [Typedef 宣告](../c-language/typedef-declarations.md) 中所述。  如需每種類型之大小的詳細資訊，請參閱[基本類型的儲存區](../c-language/storage-of-basic-types.md)。  
  
## 請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)