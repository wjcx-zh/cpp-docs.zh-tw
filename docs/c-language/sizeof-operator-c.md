---
title: sizeof 運算子 (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 1d06fc8b541cbce3771a485c8f71953be8f7d552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229515"
---
# <a name="sizeof-operator-c"></a>sizeof 運算子 (C)

**`sizeof`** 運算子會提供儲存運算元類型之物件所需的儲存空間量（以位元組為單位）。 這個運算子可以避免在您的程式中指定與電腦相關的資料大小。

## <a name="syntax"></a>語法

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>備註

運算元是 *unary-expression* 的識別項，或是類型轉換運算式 (也就是以括號括住的類型指定名稱)。 *unary-expression* 無法表示位元欄位物件、不完整的類型或函式指示項。 結果為不帶正負號的整數常數。 標準標頭檔 STDDEF.H 將此類型定義為 **size_t**。

當您將 **`sizeof`** 運算子套用至陣列識別碼時，結果會是整個陣列的大小，而不是陣列識別碼所表示的指標大小。

當您將 **`sizeof`** 運算子套用至結構或等位類型名稱，或是結構或等位類型的識別碼時，結果會是結構或等位中的位元組數目，包括內部和尾端填補。 這個大小可能包含用於對齊記憶體界限上結構或等位成員的內部和尾端填補。 因此，在加上個別成員的儲存需求之後，其結果可能無法對應計算出的大小。

如果可變大小陣列是結構的最後一個元素，則 **`sizeof`** 運算子會傳回不含陣列的結構大小。

```
buffer = calloc(100, sizeof (int) );
```

這個範例會使用 **`sizeof`** 運算子來傳遞的大小 **`int`** ，這會因電腦而異，做為名為之執行時間函式的引數 `calloc` 。 由函式傳回的值會儲存在 `buffer` 中。

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

在此範例中， `strings` 是的指標陣列 **`char`** 。 指標的數目是陣列中元素的數目，但尚未指定。 您可以使用 **`sizeof`** 運算子來計算陣列中的元素數目，藉此判斷指標數目。 **`const`** 整數值 `string_no` 會初始化為這個數位。 因為它是一個 **`const`** 值，所以 `string_no` 無法修改。

## <a name="see-also"></a>另請參閱

[C 運算子](c-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
