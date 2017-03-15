---
title: "sizeof 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sizeof_cpp"
  - "sizeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sizeof 運算子"
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sizeof 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

就類型 `char` 的大小而言，會產生其運算元的大小。  
  
> [!NOTE]
>  如需 `sizeof ...` 運算子的資訊，請參閱 [省略符號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md)。  
  
## 語法  
  
```  
sizeof unary-expression sizeof  ( type-name )  
```  
  
## 備註  
 `sizeof` 運算子的結果是 `size_t` 類型，這是 Include 檔 STDDEF.H 中定義的整數類資料類型。  這個運算子可以避免在您的程式中指定與電腦相關的資料大小。  
  
 `sizeof` 的運算元可以是下列其中一項：  
  
-   類型名稱。  若要以類型名稱來使用 `sizeof`，該名稱必須以括號括住。  
  
-   一個運算式。  與運算式搭配使用時，是否用括號來指定 `sizeof` 都可以。  並不會評估運算式。  
  
 將 `sizeof` 運算子套用至 `char` 類型的物件時，會產生 1。  將 `sizeof` 運算子套用至陣列時，會產生該陣列中的位元組總數，而不是陣列識別項所表示的指標大小。  若要取得陣列識別項所表示的指標大小，請將它當作參數傳遞至使用 `sizeof` 的函式。  例如：  
  
## 範例  
  
```  
#include <iostream>  
using namespace std;  
  
size_t getPtrSize( char *ptr )  
{  
   return sizeof( ptr );  
}  
  
int main()  
{  
   char szHello[] = "Hello, world!";  
  
   cout  << "The size of a char is: "  
         << sizeof( char )  
         << "\nThe length of " << szHello << " is: "  
         << sizeof szHello  
         << "\nThe size of the pointer is "  
         << getPtrSize( szHello ) << endl;  
}  
```  
  
## 範例輸出  
  
```  
The size of a char is: 1  
The length of Hello, world! is: 14  
The size of the pointer is 4  
```  
  
 將 `sizeof` 運算子套用至 `class`、`struct` 或 `union` 類型時，結果是該類型物件中的位元組數，加上為了讓成員對齊字邊界而加入的任何填補位元組。  在加上個別成員的儲存需求之後，其結果不一定會對應計算的大小。  [\/Zp](../build/reference/zp-struct-member-alignment.md) 編譯器選項和 [pack](../preprocessor/pack.md) pragma 會影響成員的對齊邊界。  
  
 `sizeof` 運算子絕不會產生 0，即使用於空類別也一樣。  
  
 `sizeof` 運算子不能與下列運算元搭配使用：  
  
-   函式。  \(不過，`sizeof` 可套用於函式的指標。\)  
  
-   位元欄位。  
  
-   未定義的類別。  
  
-   `void` 類型。  
  
-   以動態方式配置的陣列。  
  
-   外部陣列。  
  
-   不完整的類型。  
  
-   以括號括住的不完整類型名稱。  
  
 將 `sizeof` 運算子套用至參考時，結果相同，就像 `sizeof` 套用至物件本身一樣。  
  
 如果可變大小的陣列是結構的最後一個項目，`sizeof` 運算子會傳回不含陣列的結構大小。  
  
 `sizeof` 運算子經常用來計算陣列中的元素數目，所使用的運算式格式如下：  
  
```  
sizeof array / sizeof array[0]  
```  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)