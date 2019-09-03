---
title: 字串化運算子 (#)
ms.date: 08/29/2019
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
ms.openlocfilehash: 5a1b43198e59bc1e69cdf1b56db56be75719fe46
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216546"
---
# <a name="stringizing-operator-"></a>字串化運算子 (#)

數位記號或 "字串化" 運算子 ( **#** ) 會將巨集引數轉換為字串常值, 而不會擴充參數定義。 它只能與接受引數的宏搭配使用。 如果出現在巨集定義的型式參數之前，巨集引動過程傳入的實質引數會以引號括住並且將視為字串常值。 然後字串常值會取代巨集定義中每個字串化運算子和型式參數的組合。

> [!NOTE]
> ANSI C 標準的 Microsoft C (6.0 版和之前版本) 擴充功能之前會展開字串常值和字元常數中的巨集型式引數，但目前已不再支援此功能。 依賴此延伸模組的程式碼應該使用字串化 ( **#** ) 運算子來重寫。

會忽略第一個 token 前面的空白字元, 並遵循實際引數的最後一個 token。 在實際引數中語彙基元之間的任何空白字元，在產生的字串常值中皆會縮短為單一空白字元。 因此, 如果在實際引數中的兩個標記之間出現批註, 則會縮減為單一空白字元。 產生的字串常值會自動與任何只以空白字元分隔的相鄰字串常值串連。

此外, 如果引數中包含的字元在字串常值 (例如, 引號 (`"`) 或反斜線 (`\`) 字元) 中使用時, 通常需要有 escape 序列, 則會自動執行必要的 escape 反斜線已插入字元之前。

當 Microsoft C++字串化運算子與包含逸出序列的字串搭配使用時, 其行為不正確。 在這種情況下, 編譯器會產生[編譯器錯誤 C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md)。

## <a name="examples"></a>範例

下列範例顯示包含字串化運算子的巨集定義, 以及叫用宏的 main 函式:

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

[預處理器運算子](../preprocessor/preprocessor-operators.md)
