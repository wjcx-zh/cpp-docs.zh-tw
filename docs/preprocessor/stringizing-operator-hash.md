---
title: 字串化運算子 (#)
ms.date: 11/04/2016
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: d90d07c8f3cce6c443be0eb994db494746c00fcc
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711146"
---
# <a name="stringizing-operator-"></a>字串化運算子 (#)

數位記號或 "字串化" 運算子 ( **#** ) 會將巨集引數轉換為字串常值, 而不會擴充參數定義。 只會搭配接受引數的巨集使用。 如果出現在巨集定義的型式參數之前，巨集引動過程傳入的實質引數會以引號括住並且將視為字串常值。 然後字串常值會取代巨集定義中每個字串化運算子和型式參數的組合。

> [!NOTE]
> ANSI C 標準的 Microsoft C (6.0 版和之前版本) 擴充功能之前會展開字串常值和字元常數中的巨集型式引數，但目前已不再支援此功能。 依賴此延伸模組的程式碼應該使用字串化 ( **#** ) 運算子來重寫。

實際引數的第一個語彙基元之前和最後一個語彙基元之後的空白字元則會予以忽略。 在實際引數中語彙基元之間的任何空白字元，在產生的字串常值中皆會縮短為單一空白字元。 因此，如果在實際引數的兩個語彙基元之間出現註解，將會縮短為單一空白字元。 產生的字串常值會自動與任何僅以空白字元分隔的相鄰字串常值串連。

此外, 如果引數中包含的字元通常需要在字串常值 (例如引號 ( **"** ) 或反斜線 ( **\\** ) 字元) 中使用時的轉義順序, 則會自動插入必要的 escape 反斜線字元之前。

當 Visual C++字串化運算子與包含逸出序列的字串搭配使用時, 其行為不正確。 在這種情況下, 編譯器會產生[編譯器錯誤 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)。

## <a name="examples"></a>範例

下列範例中展示一項巨集定義，其中包含字串化運算子和叫用巨集的主函式：

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

`stringer`宏會在前置處理期間展開, 並產生下列程式碼:

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

下列範例示範如何展開巨集參數：

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>另請參閱

[前置處理器運算子](../preprocessor/preprocessor-operators.md)
