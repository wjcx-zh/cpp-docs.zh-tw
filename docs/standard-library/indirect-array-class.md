---
title: indirect_array 類別
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687925"
---
# <a name="indirect_array-class"></a>indirect_array 類別

內部的輔助類別樣板，藉由指定父 valarray 的索引子集，在定義的子集陣列之間提供作業，藉此支援屬於 valarray 子集的物件。

## <a name="syntax"></a>語法

## <a name="remarks"></a>備註

類別會描述一個物件，它會儲存 `va` 類別[valarray](../standard-library/valarray-class.md) **\<Type >** 的物件參考，以及類別 `valarray<size_t>` 的物件 `xa`，其中描述要從 `valarray<Type>` 物件選取的專案序列。

您只能藉由撰寫 `va[xa]` 格式的運算式來建立 `indirect_array<Type>` 物件。 類別 indirect_array 的成員函式的行為就像是針對 `valarray<Type>` 定義的對應函式簽章，但只有所選項目的順序會受到影響。

順序是由 xa 所組成 **。** [大小](../standard-library/valarray-class.md#size)元素，其中元素 `I` 會變成 `va` 內的索引**xa**[`I`]。

## <a name="example"></a>範例：

```cpp
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

### <a name="output"></a>Output

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>需求

**標頭：** \<valarray>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
