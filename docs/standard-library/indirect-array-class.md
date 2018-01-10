---
title: "indirect_array 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::indirect_array
dev_langs: C++
helpviewer_keywords: indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6479dbdf8e3da19581f3acbfcb9fa64f42b335cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="indirectarray-class"></a>indirect_array 類別
對於指定父代 valarray 索引子集而定義的子集陣列，可藉由提供這些子集之間的作業，支援 valarray 子集物件的內部、輔助的範本類別。  
  
## <a name="syntax"></a>語法  
  
  
  
## <a name="remarks"></a>備註  
 此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md)**\<Type>** 類別之 **va** 物件的參考與 **valarray<size_t>** 類別的 **xa** 物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的元素序列。  
  
 您只能藉由撰寫 **va[xa]** 格式的運算式來建構 **indirect_array\<Type>** 物件。 indirect_array 類別的成員函式會接著像針對 **valarray\<Type>** 定義的對應函式簽章一樣運作，不同的是，只有選取的元素序列會受到影響。  
  
 此序列是由 **xa.**[size](../standard-library/valarray-class.md#size) 元素所構成，其中元素 `I` 會變成 **va** 內的索引 **xa**[ `I`]。  
  
## <a name="example"></a>範例：  
  
```  
// indirect_array.cpp  
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
  
   // Select 2nd, 4th & 6th elements  
   // and assign a value of 10 to them  
   valarray<size_t> indx ( 3 );  
   indx [0] = 2;  
   indx [1] = 4;  
   indx [2] = 6;  
   va[indx] = 10;  
  
   cout << "The modified operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### <a name="output"></a>輸出  
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<valarray>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

