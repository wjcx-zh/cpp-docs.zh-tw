---
title: "mask_array 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::mask_array
dev_langs:
- C++
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 768ad87caf6fb3d5b8ed5574bd5f110282d795f5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="maskarray-class"></a>mask_array 類別
可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。  
  
## <a name="syntax"></a>語法  
  
  
  
## <a name="remarks"></a>備註  
 此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md)**\<Type>** 類別之 **va** 物件的參考與 [valarray\<bool>](../standard-library/valarray-bool-class.md) 類別的 **ba** 物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的元素序列。  
  
 您只能藉由撰寫 [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at) 格式的運算式來建構 **mask_array\<Type>** 物件。 mask_array 類別的成員函式會接著像針對 **valarray\<Type>** 定義的對應函式簽章一樣運作，不同的是，只有選取的元素序列會受到影響。  
  
 序列最多包含 **ba.size** 個項目。 只有在 *ba* [ **J**] 為 true 時才會包含項目 *J*。 因此，序列中的項目數會和 **ba**中的 true 項目數相同。 如果 `I` 是 **ba**中最低 true 項目的索引，則 **va**[ `I`] 便是選取之序列中的第零個項目。  
  
## <a name="example"></a>範例：  
  
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
  
### <a name="output"></a>輸出  
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<valarray>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

