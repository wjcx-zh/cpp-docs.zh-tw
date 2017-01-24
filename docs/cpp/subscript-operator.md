---
title: "註標運算子： | Microsoft Docs"
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
  - "[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算子 [C++], 註標"
  - "後置運算子"
  - "[] 運算子"
  - "註標運算子, 語法"
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 註標運算子：
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
postfix-expression [ expression ]  
```  
  
## 備註  
 後置運算式 \(也可以是主要運算式\) 後面會加上指派陣列索引的註標運算子 **\[ \]**。  
  
 如需 Managed 陣列的詳細資訊，請參閱[Arrays](../windows/arrays-cpp-component-extensions.md)。  
  
 通常，*postfix\-expression* 所代表的值是指標值 \(例如陣列識別項\)，而 *expression* 則是整數值 \(包括列舉類型\)。  不過，在語法上需要的是其中一個指標類型的運算式，另一個則是整數類型。  因此，整數值可以在 *postfix\-expression* 位置，而指標值則可以在 *expression* 的括號中，或是在註標位置。  請考慮下列程式碼片段：  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 在上述範例中，運算式 `nArray[2]` 與 `2[nArray]` 相同。  其原因是註標運算式 *e1***\[** *e2* **\]** 是由下列運算式指定：  
  
 **\*\( \(** *e2* **\)** *\+* **\(***e1***\) \)**  
  
 運算式所產生的位址不是來自位址 *e1* 的 *e2* 位元組。  相反地，這個位址會進行縮放，以產生陣列 *e2* 中的下一個物件。  例如:  
  
```  
double aDbl[2];  
```  
  
 `aDb[0]` 和 `aDb[1]` 的位址皆為 8 個位元組，即為 **double** 類型物件的大小。  此項縮放是由 C\+\+ 語言根據物件類型自動完成，其定義於[加法類運算子](../cpp/additive-operators-plus-and.md)中，其中會討論指標類型運算元的加法和減法。  
  
 註標運算式也可以擁有多個註標，如下所示：  
  
 *expression1* **\[***expression2***\] \[***expression3***\]**...  
  
 註標運算式的關聯是由左至右。  最左邊的註標運算式 *expression1***\[***expression2***\]** 會最先評估。  *expression1* 和 *expression2* 相加所產生的位址會形成指標運算式，然後 *expression3* 會加入這個指標運算式形成新的指標運算式，依此類推，直到加入最後一個註標運算式為止。  除非最後一個指標值定址為陣列類型，否則間接運算子 \(**\***\) 會在最後一個註標運算式評估之後套用。  
  
 具有多個註標的運算式會參考多維陣列的元素。  所謂的多維陣列是指其中所包含的元素也是一種陣列。  例如，三維陣列的第一個元素是具有兩個維度的陣列。  下列範例會宣告和初始化一個簡單的二維字元陣列：  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## 正數和負數註標  
 陣列的第一個元素是元素 0。  C\+\+ 陣列的範圍是從 *陣列*\[0\] 到 *陣列*\[*大小* – 1\]。  不過，C\+\+ 支援正註標和負註標。  負註標必須在陣列界限內，如果不在界限內，則無法預測結果。  下列程式碼顯示正的和負的陣列註標：  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 最後一行中的負註標可能會產生執行階段錯誤，因為它在記憶體中指出的位址比陣列的原點少 256 個位元組。  指標 `midArray` 會初始化至 `intArray` 的中央，因此能夠在上面使用正的和負的陣列索引。  陣列註標錯誤不會產生編譯時期錯誤，但是會產生無法預期的結果。  
  
 註標運算子可以交替。  因此，只要註標運算子不多載 \(請參閱*多載運算子*\)，運算式 *陣列*\[*索引*\] 和 *陣列*\[[陣列](../cpp/operator-overloading.md)\] 就一定會相等。  第一種形式是最常用的程式撰寫作法，但兩種都可以運作。  
  
## 請參閱  
 [後置運算式](../cpp/postfix-expressions.md)   
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [陣列](../cpp/arrays-cpp.md)   
 [一維陣列](../c-language/one-dimensional-arrays.md)   
 [多維陣列](../c-language/multidimensional-arrays-c.md)