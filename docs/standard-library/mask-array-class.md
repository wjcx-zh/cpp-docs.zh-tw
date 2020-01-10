---
title: mask_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689396"
---
# <a name="mask_array-class"></a>mask_array 類別

一種內部的輔助類別樣板，支援以布林運算式指定之父 valarray 子集的物件，方法是提供子集陣列之間的作業。

## <a name="syntax"></a>語法

## <a name="remarks"></a>備註

類別會描述一個物件，它會儲存對[valarray](../standard-library/valarray-class.md)類別之物件 `va` 的參考 **\<Type >** ，以及類別[valarray \<bool >](../standard-library/valarray-bool-class.md)的物件 `ba`，其中描述要選取的元素序列。從 `valarray<Type>` 物件。

您只能藉由撰寫格式為[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)的運算式來建立 `mask_array<Type>` 物件。 類別 mask_array 的成員函式的行為就像是針對 `valarray<Type>` 定義的對應函式簽章，但只有所選項目的順序會受到影響。

順序包含最多 `ba.size` 元素。 只有在 *ba* [ **J**] 為 true 時才會包含項目 *J*。 因此，序列中的元素數目會與 `ba` 中的真正元素相同。 如果 `I` 是 `ba` 中最低 true 專案的索引，則**va**[`I`] 就是選取之序列中的元素零。

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

**標頭：** \<valarray>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
