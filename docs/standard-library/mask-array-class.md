---
title: mask_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 108c942bef33e44b515d46e953c9d99274e3ce8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412978"
---
# <a name="maskarray-class"></a>mask_array 類別

可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。

## <a name="syntax"></a>語法

## <a name="remarks"></a>備註

此類別描述可儲存物件的參考`va`類別的[valarray](../standard-library/valarray-class.md)**\<型別 >**，以及物件`ba`類別的[valarray\<bool >](../standard-library/valarray-bool-class.md)，其中描述要從選取的元素序列`valarray<Type>`物件。

您建構`mask_array<Type>`物件只能藉由撰寫運算式的形式[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)。 Mask_array 類別的成員函式行為接著便會像對應的函式簽章定義`valarray<Type>`，不過只有選取的元素序列會受到影響。

序列最多包含`ba.size`項目。 只有在 *ba* [ **J**] 為 true 時才會包含項目 *J*。 因此，有多個序列中項目中的 true 項`ba`。 如果`I`中最低 true 項目的索引`ba`，然後**va**[ `I`] 是選取之序列中的零個項目。

## <a name="example"></a>範例

```cpp
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

### <a name="output"></a>Output

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
