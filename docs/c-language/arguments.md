---
title: 引數
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e60a7935cdddc116848b64461b064c5fd5cdd00a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313512"
---
# <a name="arguments"></a>引數

函式呼叫中的引數具有以下格式：

> *運算式* **（** *運算式清單*<SUB>opt</SUB> **）** /* 函式呼叫 */

在函式呼叫中，*expression-list* 是運算式的清單 (以逗號分隔)。 這些後方運算式的值為傳遞至函式的引數。 如果函式不接受引數，*expression-list* 應該包含關鍵字 `void`。

引數可以是任何基本、結構、等位或指標類型的值。 所有引數皆以傳值方式傳遞。 這表示引數的複本已指派至相對應的參數。 函式並不知道所傳遞引數的實際記憶體位置。 函式會使用此複本，而不影響原始衍生來源的變數。

雖然您無法將陣列或函式做為引數傳遞，但是您可以將指標傳遞至這些項目。 指標可讓函式以傳址方式存取值。 由於變數的指標保留變數的位址，因此函式可以使用此位址存取變數的值。 即使陣列和函式不能當做引數傳遞，指標引數仍可讓函式存取陣列和函式。

引數求值的順序在不同編譯器和不同最佳化層級下可能會有所不同。 不過，在輸入函式之前，會先完全求出引數以及任何副作用的值。 如需關於副作用的詳細資訊，請參閱[副作用](../c-language/side-effects.md)。

函式呼叫中的 *expression-list* 已經求出值，並且會在函式呼叫中的每個引數上執行一般算術轉換。 如果原型可用，產生的引數類型會與原型的對應參數相等。 如果不相符，則會執行轉換或者發出診斷訊息。 參數也會進行一般算術轉換。

除非函式的原型或定義明確指定可變數目的引數，否則 *expression-list* 中的運算式數目都必須與參數數目相符。 在這種情況下，編譯器將檢查與參數清單中類型名稱數量相等數量的引數，並視需要進行轉換，如上所述。 如需詳細資訊，請參閱[使用可變數目的引數呼叫](../c-language/calls-with-a-variable-number-of-arguments.md)。

如果原型的參數清單只包含關鍵字 `void`，編譯器會預期函式呼叫中沒有引數且定義中沒有參數。 如果找到任何引數，則會發出診斷訊息。

## <a name="example"></a>範例

這個範例使用指標做為引數：

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

在此範例中，`swap` 函式在 `main` 宣告為具有兩個引數，分別由識別項 `num1` 和 `num2` 表示，兩者都是指向 `int` 值的指標。 在這個原型樣式定義中的參數 `num1` 和 `num2` 也宣告為指向 `int` 類型值的指標。

在函式呼叫中

```C
swap( &x, &y )
```

`x` 位址儲存於 `num1`，而 `y` 位址則儲存於 `num2`中。 現在相同位置中存在兩個名稱或「別名」。 在 `*num1` 中對 `*num2` 和 `swap` 的參考，實際上是在 `x` 中對 `y` 和 `main` 的參考。 在 `swap` 中的指派實際上會交換 `x` 和 `y` 的內容。 因此，`return` 陳述式並不是必要的。

由於 `swap` 原型包含每個參數的引數類型，因此編譯器會對 `swap` 的引數執行類型檢查。 原型和定義括號的內容識別項可能相同或不同。 引數類型與原型和定義中的參數清單都相符是很重要的。

## <a name="see-also"></a>請參閱

[函式呼叫](../c-language/function-calls.md)
