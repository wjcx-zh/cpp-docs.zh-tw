---
title: "mask_array 類別 | Microsoft Docs"
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
  - "std.mask_array"
  - "mask_array"
  - "std::mask_array"
  - "valarray/std::mask_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mask_array 類別"
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mask_array 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。  
  
## 語法  
  
```  
template<class Type>  
   class mask_array {  
public:  
   typedef Type value_type;  
   void operator=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator=(  
      const Type& x  
   ) const;  
  
   void operator*=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator/=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator%=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator+=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator-=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator^=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator&=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator|=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator<<=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator>>=(  
      const valarray<Type>& x  
   ) const;  
  
// The rest is private or implementation defined  
}  
```  
  
## 備註  
 此類別會描述物件，該物件會儲存類別 [valarray](../standard-library/valarray-class.md)**\<類型\>** 的 **va** 物件參考，以及類別 [valarray\<bool\>](../standard-library/valarray-bool-class.md) 的 **ba** 物件參考，後者描述從 **valarray\<類型\>** 物件選取項目的序列。  
  
 您建構 **mask\_array\<類型\>** 物件的方法，只能藉由撰寫 [va&#91;ba&#93;](../Topic/valarray::operator.md) 格式的運算式來完成。 mask\_array 類別的成員函式行為接著便會像是針對 **valarray\<類型\>** 定義的對應函式簽章一樣，不過只有選取的項目序列會受到影響。  
  
 序列最多包含 **ba.size** 個項目。 只有在 **ba**\[*J*\] 為 true 時才會包含項目 *J*。 因此，序列中的項目數會和 **ba** 中的 true 項目數相同。 如果 `I` 是 **ba** 中最低 true 項目的索引，則 **va**\[`I`\] 便是選取之序列中的第零個項目。  
  
## 範例：  
  
```  
// mask_array.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // Use masked subsets to assign a value of 10  
   // to all elements grrater than 3 in value  
   va [va > 3 ] = 10;  
   cout << "The modified operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### 輸出  
  
```  
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The modified operand valarray is:  ( 0 -1 2 -1 10 -1 10 -1 10 -1 ).  
```  
  
## 需求  
 **標頭：**\<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)