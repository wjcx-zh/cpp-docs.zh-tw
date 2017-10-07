---
title: "陣列 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: efd124254ece8f863afee13e132eea7945525a0e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="arrays-c"></a>陣列 (C++)
陣列是同類物件的集合。 最簡單的陣列案例就是向量，可以依照下列順序宣告：  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. 宣告規範：  
  
-   選擇性的儲存類別規範。  
  
-   選擇性**const**及/或`volatile`規範。  
  
-   陣列元素的類型名稱。  
  
 2. 宣告子：  
  
-   識別碼。  
  
-   方括號括住的整數類資料類型常數運算式**[]。** 如果使用其他方括號宣告多個維度，常數運算式可以省略第一方括號組。  
  
-   括住常數運算式的選擇性額外括號。  
  
 3. 選擇性的初始設定式。  請參閱[初始設定式](../cpp/initializers.md)。  
  
 陣列中元素的數目是由常數運算式提供。 陣列中的第一個項目是第 0 個元素，而最後一個項目 (*n*-1) 項目，其中* n *是陣列可以包含的元素數目。 *常數運算式*必須屬於整數型別，而且必須大於 0。 只有當陣列中的最後一個欄位的大小為零的陣列是合法`struct`或**union**而且已啟用 Microsoft 擴充功能 (/Ze) 時。  
  
 下列範例將示範如何在執行階段定義陣列：  
  
```  
// arrays.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main() {  
   using namespace std;  
   int size = 3, i = 0;  
  
   int* myarr = new int[size];  
  
   for (i = 0 ; i < size ; i++)  
      myarr[i] = 10;  
  
   for (i = 0 ; i < size ; i++)  
      printf_s("myarr[%d] = %d\n", i, myarr[i]);  
  
   delete [] myarr;  
}  
```  
  
 陣列是衍生類型，因此可以從任何其他衍生或基本類型建構，但不包括函式、參考和 `void`。  
  
 從其他陣列建構的陣列是多維陣列。 這些多維陣列是藉由依序放置多個包含括號的常數運算式所指定。 例如，以下列宣告為例：  
  
```  
int i2[5][7];  
```  
  
 它會指定類型為 `int`、在概念上以五列七行的二維矩陣排列的陣列，如下圖所示：  
  
 ![多重 & #45 的概念性配置; 二維陣列](../cpp/media/vc38rc1.gif "vc38RC1")  
多維陣列的概念性配置  
  
 在宣告中的多維陣列初始設定式清單 (如所述[初始設定式](../cpp/initializers.md))，可以省略指定第一個維度界限的常數運算式。 例如:   
  
```  
// arrays2.cpp  
// compile with: /c  
const int cMarkets = 4;  
// Declare a float that represents the transportation costs.  
double TransportCosts[][cMarkets] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }  
};  
```  
  
 上述宣告會定義一個三列四行的陣列。 資料列代表工廠，資料行則代表工廠出貨的市場。 值是從工廠到市場的運費。 陣列的第一個維度會被省略，但編譯器會藉由檢查初始設定式填入該維度。  
  
 本節主題：  
  
-   [使用陣列](../cpp/using-arrays-cpp.md)  
  
-   [運算式中的陣列](../cpp/arrays-in-expressions.md)  
  
-   [註標運算子的解譯](../cpp/interpretation-of-subscript-operator.md)  
  
-   [陣列類型的間接取值](../cpp/indirection-on-array-types.md)  
  
-   [C++ 陣列的排序](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>範例  
 省略多維陣列中第一個維度之界限規格的技術也可用於函式宣告，如下所示：  
  
```  
// multidimensional_arrays.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <limits>   // Includes DBL_MAX  
#include <iostream>  
  
const int cMkts = 4, cFacts = 2;  
  
// Declare a float that represents the transportation costs  
double TransportCosts[][cMkts] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }    
};  
  
// Calculate size of unspecified dimension  
const int cFactories = sizeof TransportCosts /  
                  sizeof( double[cMkts] );  
  
double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);  
  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   double MinCost;  
  
   if (argv[1] == 0) {  
      cout << "You must specify the number of markets." << endl;  
      exit(0);  
   }  
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);  
   cout << "The minimum cost to Market " << argv[1] << " is: "  
       << MinCost << "\n";  
}  
  
double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {  
   double MinCost = DBL_MAX;  
  
   for( int i = 0; i < cFacts; ++i )  
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?  
         MinCost : TransportCosts[i][Mkt];  
  
   return MinCost;  
}  
```  
  
```Output  
The minimum cost to Market 3 is: 17.29  
```  
  
## <a name="comments"></a>註解  
 若撰寫 `FindMinToMkt` 函式，加入新的工廠時就不需要變更任何程式碼，只需要重新編譯。  
  
## <a name="see-also"></a>另請參閱  
 
