---
title: "預設引數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引數 [C++], 預設"
  - "引數 [C++], 函式"
  - "宣告函式, 宣告子"
  - "預設引數"
  - "預設值 [C++], 引數"
  - "函式宣告子"
  - "函式 [C++], 預設引數"
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 預設引數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在許多情況下，函式的引數不常使用，因此使用預設值即已足夠。  為解決此問題，預設引數機能只能用於指定在特定呼叫中具有意義之函式的這些引數。  為了說明這個概念，請參考[函式多載](../cpp/function-overloading.md)中的範例。  
  
```  
// Prototype three print functions.  
int print( char *s );                  // Print a string.  
int print( double dvalue );            // Print a double.  
int print( double dvalue, int prec );  // Print a double with a  
//  given precision.  
```  
  
 許多應用程式可以提供 `prec` 適用的合理預設值，因此不需要兩個函式：  
  
```  
// Prototype two print functions.  
int print( char *s );                    // Print a string.  
int print( double dvalue, int prec=2 );  // Print a double with a  
//  given precision.  
```  
  
 稍微變更 `print` 函式的實作，以反映 **double** 類型只能有一個此類函式存在的事實：  
  
```  
// default_arguments.cpp  
// compile with: /EHsc /c  
  
// Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
  
#include <iostream>  
#include <math.h>  
using namespace std;  
  
int print( double dvalue, int prec ) {  
   // Use table-lookup for rounding/truncation.  
   static const double rgPow10[] = {   
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,  
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6  
   };  
   const int iPowZero = 6;  
   // If precision out of range, just print the number.  
   if( prec >= -6 && prec <= 7 )  
      // Scale, truncate, then rescale.  
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *  
      rgPow10[iPowZero - prec];  
   cout << dvalue << endl;  
   return cout.good();  
}  
```  
  
 若要叫用新的 `print` 函式，請使用如下所示的程式碼：  
  
```  
print( d );    // Precision of 2 supplied by default argument.  
print( d, 0 ); // Override default argument to achieve other  
//  results.  
```  
  
 使用預設引數時請注意下列重點：  
  
-   預設引數僅用於忽略結尾引數的函式呼叫，這些引數必須是最後的引數。  因此，下列程式碼是不合法的：  
  
    ```  
    int print( double dvalue = 0.0, int prec );  
    ```  
  
-   即使重新定義與原始定義完全相同，之後宣告時也不能重新定義預設引數。  因此，下列程式碼會產生錯誤：  
  
    ```  
    // Prototype for print function.  
    int print( double dvalue, int prec = 2 );  
  
    ...  
  
    // Definition for print function.  
    int print( double dvalue, int prec = 2 )  
    {  
    ...  
    }  
    ```  
  
     這個程式碼的問題在於定義中的函式宣告會重新定義 `prec` 的預設引數。  
  
-   您可以利用之後的宣告加入其他預設引數。  
  
-   可以對函式指標提供預設引數。  例如:  
  
    ```  
    int (*pShowIntVal)( int i = 0 );  
    ```  
  
## 請參閱  
 [C\+\+ 抽象宣告子](http://msdn.microsoft.com/zh-tw/e7e18c18-0cad-4450-942b-d27e1d4dd088)