---
title: 函數呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: cce1a888f3e1224822ab4e97c67bf59da4c46fc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334566"
---
# <a name="function-calls"></a>函數呼叫

「函式呼叫」** 是一種運算式，會將控制項和引數 (如果有的話) 傳遞至函式，且具有下列形式：

*運算式*（*運算式清單*<sub>opt</sub>）

其中 *expression* 是函式名稱，或會評估為函式位址，而 *expression-list* 是運算式的清單 (以逗號分隔)。 這些後方運算式的值為傳遞至函式的引數。 如果函式不會傳回值，那麼您會將它宣告為傳回 `void` 的函式。

如果宣告出現在函式呼叫之前，但是未提供有關參數的任何資訊，則所有未宣告的引數都會直接進行一般算術轉換。

> [!NOTE]
> 函式引數清單中的運算式可以依照任意順序求值，因此，若引數的值可能因其他引數的副作用而變更，則這類引數會擁有未定義的值。 函式呼叫運算子所定義的序列點僅保證，引數清單中的所有副作用都會先經過求值，控制項才會傳遞至呼叫的函式  （請注意，引數在堆疊上推送的順序是不同的）。如需詳細資訊，請參閱[序列點](../c-language/c-sequence-points.md)。

所有函式呼叫的唯一需求就是，括號前面的運算式必須求出函式位址值。 這表示，函式可以透過任何函式指標運算式呼叫。

## <a name="example"></a>範例

這個範例將示範從 `switch` 陳述式呼叫的函式呼叫：

```
int main()
{
    /* Function prototypes */

    long lift( int ), step( int ), drop( int );
    void work( int number, long (*function)(int i) );

    int select, count;
    .
    .
    .
    select = 1;
    switch( select )
    {
        case 1: work( count, lift );
                break;

        case 2: work( count, step );
                break;

        case 3: work( count, drop );
                /* Fall through to next case */
        default:
                break;
    }
}

/* Function definition */

void work( int number, long (*function)(int i) )
{
    int i;
    long j;

    for ( i = j = 0; i < number; i++ )
            j += ( *function )( i );
}
```

在這個範例中，`main` 中的函式呼叫 

```
work( count, lift );
```

會將整數變數 `count` 和函式 `lift` 的位址傳遞至函式 `work`。 請注意，函式位址僅透過指定函式識別項進行傳遞，因為函式識別項會求出指標運算式的值。 若要以此方式使用函式識別項，則必須在使用識別項之前宣告或定義函式，否則無法辨識識別項。 在此案例中，`work` 函式的開頭會指定 `main` 的原型。

`work` 中的 `function` 參數會宣告為函式的指標，該函式會採用一個 `int` 引數並傳回 **long** 值。 參數名稱前後必須加上括號，若沒有括號，則宣告會指定傳回 **long** 值指標的函式。

`work` 函式會使用下列函式呼叫，從 **for** 迴圈內呼叫選取的函式：

```
( *function )( i );
```

其中一個引數 `i` 會傳遞至呼叫的函式。

## <a name="see-also"></a>請參閱

[函式](../c-language/functions-c.md)
