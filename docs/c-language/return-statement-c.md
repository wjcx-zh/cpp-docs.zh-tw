---
title: return 陳述式 (C)
description: C 語言 return 語句會結束函式執行，並選擇性地將值傳回給呼叫者。
ms.date: 06/10/2020
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: 7d518aa17185c96de15c8f9aa9b65ae5c72bd014
ms.sourcegitcommit: 01b911613606c3fc92cbd9ca48cca6046a7e8258
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84716290"
---
# <a name="return-statement-c"></a>return 陳述式 (C)

語句會結束函式 **`return`** 的執行，並將控制權傳回給呼叫的函式。 執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。 **`return`** 語句可以將值傳回給呼叫函數。 如需詳細資訊，請參閱傳回[型](../c-language/return-type.md)別。

## <a name="syntax"></a>Syntax

> *跳躍語句*： \
> &nbsp;&nbsp;&nbsp;&nbsp;**`return`***運算式*&#8203;<sub>opt</sub>**`;`**

*expression* 的值 (如果有) 會傳回至呼叫函式。 如果省略 *expression*，則函式的傳回值會是未定義。 此運算式 (如果有) 會先評估，再轉換為函式所傳回的類型。 當 **`return`** 語句在具有傳回類型的函式中包含運算式時 **`void`** ，編譯器會產生警告，而且不會評估運算式。

如果 **`return`** 函式定義中沒有出現任何語句，則在執行所呼叫函式的最後一個語句之後，控制項會自動返回呼叫函式。 在此情況下，所呼叫函式的傳回值會是未定義。 如果函式的傳回型別不是 **`void`** ，則會是嚴重的錯誤，而且編譯器會列印警告診斷訊息。 如果函式有傳回 **`void`** 型別，則此行為是正常的，但可能被視為不佳的樣式。 請使用純文字 **`return`** 語句來清除意圖。

做為良好的工程實務，請一律指定函式的傳回型別。 如果不需要傳回值，請宣告函式以擁有傳回 **`void`** 型別。 如果未指定傳回型別，C 編譯器會假設為的預設傳回型別 **`int`** 。

許多程式設計人員會使用括弧來括住語句的*expression*引數 **`return`** 。 不過，C 不需要括弧。

編譯器可能會發出有關無法連線之程式碼的警告診斷訊息（如果它發現在語句之後的任何語句） **`return`** 。

在 **`main`** 函數中， **`return`** 語句和運算式是選擇性的。 傳回的值會發生什麼情況，如果有指定，則取決於執行。 **Microsoft 特定**： microsoft C 執行會將運算式值傳回給叫用程式的進程，例如 *`cmd.exe`* 。 如果未 **`return`** 提供任何運算式，Microsoft C 執行時間會傳回值，表示成功（0）或失敗（非零值）。

## <a name="example"></a>範例

這個範例是幾個部分中的一個程式。 它會示範 **`return`** 語句，以及如何使用它來結束函數執行，以及選擇性地傳回值。

```C
// C_return_statement.c
// Compile using: cl /W4 C_return_statement.c
#include <limits.h>      // for INT_MAX
#include <stdio.h>       // for printf

long long square( int value )
{
    // Cast one operand to long long to force the
    // expression to be evaluated as type long long.
    // Note that parentheses around the return expression
    // are allowed, but not required here.
    return ( value * (long long) value );
}
```

函 `square` 式會以較寬的類型傳回其引數的平方，以避免發生算術錯誤。 **Microsoft 特定**：在 microsoft C 中， **`long long`** 類型夠大，足以容納兩個值的乘積， **`int`** 而不會溢位。

運算式周圍的括弧 **`return`** `square` 會評估為運算式的一部分，而且不需要 **`return`** 語句。

```C
double ratio( int numerator, int denominator )
{
    // Cast one operand to double to force floating-point
    // division. Otherwise, integer division is used,
    // then the result is converted to the return type.
    return numerator / (double) denominator;
}
```

函式會傳回 `ratio` 其兩個 **`int`** 引數的比率做為浮點 **`double`** 值。 **`return`** 運算式會強制使用浮點運算，方法是將其中一個運算元轉換成 **`double`** 。 否則，將會使用整數除法運算子，而小數部分則會遺失。

```C
void report_square( void )
{
    int value = INT_MAX;
    long long squared = 0LL;
    squared = square( value );
    printf( "value = %d, squared = %lld\n", value, squared );
    return; // Use an empty expression to return void.
}
```

函 `report_square` 式會呼叫 `square` ，其參數值為 `INT_MAX` 符合的最大帶正負號整數值 **`int`** 。 **`long long`** 結果會儲存在中 `squared` ，然後再列印。 `report_square`函數有傳回 **`void`** 型別，因此它的語句中沒有運算式 **`return`** 。

```C
void report_ratio( int top, int bottom )
{
    double fraction = ratio( top, bottom );
    printf( "%d / %d = %.16f\n", top, bottom, fraction );
    // It's okay to have no return statement for functions
    // that have void return types.
}
```

`report_ratio`函數會 `ratio` 使用和的參數值呼叫 `1` `INT_MAX` 。 **`double`** 結果會儲存在中 `fraction` ，然後再列印。 `report_ratio`函數有傳回 **`void`** 型別，因此不需要明確地傳回值。 執行「 `report_ratio` 落在底部」並不會傳回任何值給呼叫者。

```C
int main()
{
    int n = 1;
    int x = INT_MAX;

    report_square();
    report_ratio( n, x );

    return 0;
}
```

函式會 **`main`** 呼叫兩個函數： `report_square` 和 `report_ratio` 。 As `report_square` 不接受任何參數並傳回 **`void`** ，我們不會將其結果指派給變數。 同樣地，會傳回 `report_ratio` **`void`** ，因此我們不會儲存其傳回值。 在上述每個函式呼叫之後，會在下一個語句繼續執行。 然後傳回的 **`main`** 值 `0` （通常用來報告成功）來結束程式。

若要編譯範例，請建立名為的原始程式碼檔 *`C_return_statement.c`* 。 然後，依照顯示的順序複製所有範例程式碼。 儲存檔案，並使用命令在開發人員命令提示字元視窗中進行編譯：

**`cl /W4 C_return_statement.c`**

然後，若要執行範例程式碼，請 **`C_return_statement.exe`** 在命令提示字元中輸入。 此範例的輸出如下所示：

```Output
value = 2147483647, squared = 4611686014132420609
1 / 2147483647 = 0.0000000004656613
```

## <a name="see-also"></a>另請參閱

[陳述式](../c-language/statements-c.md)
