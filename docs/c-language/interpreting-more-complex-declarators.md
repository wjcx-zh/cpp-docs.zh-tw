---
title: 解譯更複雜的宣告子
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 13c81728f02963863b641348b58380da099b0013
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148240"
---
# <a name="interpreting-more-complex-declarators"></a>解譯更複雜的宣告子

您可以用括號括住所有宣告子，以指定「複雜宣告子」的特定解譯。 複雜宣告子是以一個以上的陣列、指標或函式修飾詞限定的識別項。 您可以將各種不同的陣列、指標及函式修飾詞組合套用至單一識別項。 通常可使用 `typedef` 簡化宣告。 請參閱 [Typedef 宣告](../c-language/typedef-declarations.md)。

在解譯複雜宣告子時，方括號和括號 (即在識別項右邊的修飾詞) 的優先順序高於星號 (即在識別項左邊的修飾詞)。 方括號和括號的優先順序相同，並且都是由左至右關聯。 在完整解譯宣告子之後，會在最後一個步驟套用類型指定名稱。 您可以使用括號覆寫預設的關聯順序並強制執行特定解譯。 但是，請勿使用括號括住識別項名稱本身。 否則，會被錯誤解譯為參數清單。

解譯複雜宣告子的一個簡單方式是透過下列四個步驟「從內而外」進行讀取：

1. 從識別項開始，直接尋找方括號或括號 (如果有的話) 的右方。

1. 解譯這些方括號或括號，然後在左方尋找星號。

1. 如果您在任何階段遇到右括號，請返回並將規則 1 和 2 套用到括號內的所有內容。

1. 套用類型指定名稱。

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

在本範例中，步驟是依序編號，並可解譯為如下：

1. `var` 識別項宣告為

1. 指標指向

1. 函式傳回

1. 指標指向

1. 10 個元素的陣列，包括

1. 其指標

1. `char` 值。

## <a name="examples"></a>範例

下列範例說明其他複雜宣告，並示範括號如何影響宣告的意義。

```
int *var[5]; /* Array of pointers to int values */
```

陣列修飾詞的優先順序高於指標修飾詞，因此會將 `var` 宣告為陣列。 指標修飾詞套用至陣列元素的類型；因此，陣列元素是 `int` 值的指標。

```
int (*var)[5]; /* Pointer to array of int values */
```

在此 `var` 宣告中，指標修飾詞加了括號，因此優先順序高於陣列修飾詞，而 `var` 則被宣告為五個 `int` 值之陣列的指標。

```
long *var( long, long ); /* Function returning pointer to long */
```

函式修飾詞的優先順序也比指標修飾詞高，因此，這個針對 `var` 的宣告會將 `var` 宣告為將指標傳回 **long** 值的函式。 函式會宣告為採用兩個 **long** 值做為引數。

```
long (*var)( long, long ); /* Pointer to function returning long */
```

這個範例與上一個範例類似。 指標修飾詞加上了括號，因此優先順序高於函式修飾詞，因此 `var` 被宣告為傳回 **long** 值之函式的指標。 同樣地，函式會採用兩個 **long** 引數。

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

陣列的元素不可為函式，不過，這個宣告會示範如何將指標陣列改宣告為函式。 在此範例中，`var` 會宣告為有五個指標之陣列，且此陣列屬於傳回有兩個成員之結構的函式。 函式的引數會宣告為兩個相同結構類型 (`both`) 的函式。 請注意，`*var[5]` 一定要加上括號。 如果不加括號，宣告即為無效的函式陣列宣告，如下所示：

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

下列陳述式會宣告指標陣列。

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name` 陣列會將 50 個元素歸納在多維陣列中。 這些元素是本身為常數之指標的指標。 這個常數指標會指向沒有參數的函式，而且傳回不帶正負號類型的指標。

下一個範例中的函式會傳回有三個 **double** 值的陣列指標。

```
double ( *var( double (*)[3] ) )[3];
```

在這個宣告中，由於傳回陣列的函式無效，因此函式會傳回陣列指標。 這裡的 `var` 會宣告為傳回有三個 **double** 值之陣列指標的函式。 `var` 函式會採用一個引數。 該引數和傳回值一樣，是有三個 **double** 值的陣列指標。 引數類型會由複雜的 *abstract-declarator* 指定。 引數類型中的星號必須加上括號；若未加上括號，引數類型會成為針對 **double** 值之三個指標的陣列。 如需抽象宣告子的討論和範例，請參閱[抽象宣告子](../c-language/c-abstract-declarators.md)。

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

如上述範例所示，指標可以指向另一個指標，而且陣列可以包含作為元素的陣列。 在這裡，`var` 是有五個元素的陣列。 每個項目都是五個元素陣列指標的指標與有兩個成員的等位。

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

這個範例示範括號位置如何改變宣告的意義。 在此範例中，`var` 是等位五個元素陣列指標的五個元素陣列指標。 如需如何使用 `typedef` 避免複雜宣告的範例，請參閱 [Typedef 宣告](../c-language/typedef-declarations.md)。

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
