---
title: C 關係和等號比較運算子
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 9ae5a31b5f4b81876d2fe518635a9766d2b5323c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227942"
---
# <a name="c-relational-and-equality-operators"></a>C 關係和等號比較運算子

二元關係運算子和相等運算子會比較其第一個運算元與第二個運算元，以測試指定的關聯性是否有效。 如果測試的關聯性是 true，則關聯運算式的結果為 1，如果是 false，結果即為 0。 結果的類型為 **`int`** 。

**語法**

*關聯式運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式* **&lt;***shift 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式* **>***shift 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式* **&lt;=***shift 運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關聯式運算式* **>=***shift 運算式*

*equality-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*等號比較運算式* **==***關聯式運算式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

關係運算式和相等運算子會測試下列關聯性：

|運算子|測試的關聯性|
|--------------|-------------------------|
|**&lt;**|第一個運算元小於第二個運算元|
|**>**|第一個運算元大於第二個運算元|
|**&lt;=**|第一個運算元小於或等於第二個運算元|
|**>=**|第一個運算元大於或等於第二個運算元|
|**==**|第一個運算元等於第二個運算元|
|**!=**|第一個運算元不等於第二個運算元|

上列清單中前四個運算子的優先順序高於相等運算子 (`==` 和 `!=`)。 請參閱表 [C 運算子的優先順序和關聯性](../c-language/precedence-and-order-of-evaluation.md)中的優先順序資訊。

運算元的類型可能是整數類型、浮點類型或指標類型。 運算元的類型可以不同。 關係運算子會對整數和浮點類型運算元執行一般算術轉換。 此外，您可以使用下列運算元類型組合搭配關係運算子和相等運算子：

- 任何關係運算子或相等運算子的運算元都可以是相同類型的指標。 針對相等運算子 (`==`) 和不等運算子 (`!=`)，比較結果會指出兩種指標是否定址相同的記憶體位置。 針對其他關係運算子（ **\<**, **>** ， **\<**=, and **>** =），比較的結果會指出所指向物件的兩個記憶體位址的相對位置。 關係運算子只會比較位移。

   指標比較的定義僅適用於同一物件的部分。 如果指標參考陣列的成員，比較就相當於對應註標的比較。 第一個陣列元素的位址「小於」最後一個元素的位址。 以結構來說，之後宣告的結構成員指標「大於」之前在結構中宣告的成員指標。 相等位的成員指標是相等的。

- 指標值可以與常數值 0 進行相等比較 (`==`) 或不等比較 (`!=`)。 值為 0 的指標稱為「Null」指標；也就是說，該指標不指向有效的記憶體位置。

- 等號比較運算子會遵循與關聯式運算子相同的規則，但允許額外的可能性：指標可以與值為0的常數整數運算式，或指向的指標 **`void`** 。 如果兩個指標都是 Null 指標，則比較結果為相等。 相等運算子會比較區段和位移二者。

## <a name="examples"></a>範例

以下範例說明關係運算子和相等運算子。

```C
int x = 0, y = 0;
if ( x < y )
```

因為 `x` 和 `y` 相等，因此這個範例中的運算式產生的值會是 0。

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

這個範例中的片段會將 `array` 的每個元素設為 Null 字元常數。

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

這些陳述式會宣告名為 `col` 且有 `color` 標記的列舉變數。 無論何時，此變數可能包含整數值 0、1 或 2，代表其中一個列舉元素會設定 `color`：分別為紅色、白色或綠色。 如果 `col` 在執行語句時包含 0 **`if`** ，則會執行視而定的任何語句 **`if`** 。

## <a name="see-also"></a>另請參閱

[關係運算子： \<, > 、\<=, and >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[等號比較運算子： = = 和！ =](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
