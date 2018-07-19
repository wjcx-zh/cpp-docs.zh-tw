---
title: indirect_array 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::indirect_array
dev_langs:
- C++
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 676cc8ea493d113e9ef8a6f85108fdf3bad6ce5f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959503"
---
# <a name="indirectarray-class"></a>indirect_array 類別

對於指定父代 valarray 索引子集而定義的子集陣列，可藉由提供這些子集之間的作業，支援 valarray 子集物件的內部、輔助的範本類別。

## <a name="syntax"></a>語法

## <a name="remarks"></a>備註

此類別描述可儲存物件的參考`va`類別的[valarray](../standard-library/valarray-class.md)**\<型別 >**，以及物件`xa`類別的`valarray<size_t>`，其中描述要從選取的元素序列`valarray<Type>`物件。

您建構`indirect_array<Type>`只能藉由撰寫運算式的格式物件`va[xa]`。 Indirect_array 類別的成員函式行為接著便會像對應的函式簽章定義`valarray<Type>`，不過只有選取的元素序列會受到影響。

序列組成**xa。**[大小](../standard-library/valarray-class.md#size)項目，其中項目`I`會變成索引**xa**[ `I`] 內`va`。

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

### <a name="output"></a>輸出

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
