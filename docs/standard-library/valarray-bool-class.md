---
title: "valarray&lt;bool&gt; 類別 | Microsoft Docs"
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
  - "valarray<bool>"
  - "valarray/std::valarray<bool>"
  - "std::valarray<bool>"
  - "std.valarray<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray<bool> 類別"
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
caps.latest.revision: 14
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# valarray&lt;bool&gt; 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 **valarray\<Type\>** 的特定版本到型別 `bool`的項目。  
  
## 語法  
  
```  
  
class valarray<bool>  
  
```  
  
## 範例  
  
```  
// valarray_bool.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaBool ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )   
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )   
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )   
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaBool = ( vaL < vaR );  
   cout << "The result of the less-than comparison "  
   << "test is the\n valarray<bool>: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaBool [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
  **最初左 valarray 如下:\(0 1 \-2 3 \-4 5 \-6 7 \-8 9\)。**  
**最初正確 valarray 如下:\(0 1 2 3 4 5 6 7 8 9\)。**  
**結果的小於比較測試是**  
 **valarraybool\<\>:\(0 0 1 0 1 0 1 0 1 0\)。**   
## 需求  
 **標頭：** \<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [valarray 類別](../standard-library/valarray-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)