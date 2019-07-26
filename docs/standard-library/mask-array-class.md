---
title: mask_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 9da5e3593288be02819330e11b60e306784054dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460144"
---
# <a name="maskarray-class"></a>mask_array 類別

可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。

## <a name="syntax"></a>語法

## <a name="remarks"></a>備註

類別描述的物件會儲存`va` [valarray](../standard-library/valarray-class.md)  **\<> 類型**之物件的參考, 以及[\<valarray bool >](../standard-library/valarray-bool-class.md)的物件`ba` , 其描述要從`valarray<Type>`物件選取的專案序列。

您只能藉`mask_array<Type>`由撰寫格式為[va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)的運算式來建立物件。 類別 mask_array 的成員函式的行為就像是針對定義的`valarray<Type>`對應函式簽章, 但只有所選項目的順序會受到影響。

順序包含最多`ba.size`個元素。 只有在 *ba* [ **J**] 為 true 時才會包含項目 *J*。 因此, 序列中的元素數目會與中`ba`的真正元素相同。 如果`I`是中`ba`最低 true 專案的索引, 則**va**[ `I`] 是選取之序列中的元素零。

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

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
