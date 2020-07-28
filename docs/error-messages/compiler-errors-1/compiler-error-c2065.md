---
title: 編譯器錯誤 C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 68817498d6f29ef5982b72a2fee4e64a4423ccde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214811"
---
# <a name="compiler-error-c2065"></a>編譯器錯誤 C2065

> '*identifier*'：未宣告的識別碼

編譯器找不到識別碼的宣告。 此錯誤的可能原因有很多。 最常見的 C2065 原因是識別碼尚未宣告、識別碼拼錯、宣告識別碼的標頭並未包含在檔案中，或識別碼遺漏範圍限定詞，例如， `cout` 而不是 `std::cout` 。 如需 c + + 中宣告的詳細資訊，請參閱宣告[和定義（c + +）](../../cpp/declarations-and-definitions-cpp.md)。

以下是一些更詳細的常見問題和解決方案。

## <a name="the-identifier-is-undeclared"></a>未宣告識別碼

如果識別碼是變數或函式名稱，您必須先將它宣告，才能使用它。 函式宣告也必須包含其參數的類型，才能使用函數。 如果變數是使用所宣告 **`auto`** ，則編譯器必須能夠從其初始化運算式推斷型別。

如果識別碼是類別或結構的成員，或是在命名空間中宣告，則必須由類別或結構名稱限定，或命名空間名稱（當在結構、類別或命名空間範圍之外使用時）。 或者，命名空間必須由指示詞帶入範圍 **`using`** `using namespace std;` ，例如，或成員名稱必須由宣告帶入範圍 **`using`** ，例如 `using std::string;` 。 否則，不合格的名稱會被視為目前範圍中未宣告的識別碼。

如果識別碼是使用者自訂類型的標記，例如 **`class`** 或 **`struct`** ，則必須先宣告標記的類型，才能使用它。 例如，宣告 `struct SomeStruct { /*...*/ };` 必須存在，您才能 `SomeStruct myStruct;` 在程式碼中宣告變數。

如果識別碼是類型別名，則必須使用宣告或使用宣告來宣告類型 **`using`** **`typedef`** 。 例如，您必須先宣告， `using my_flags = std::ios_base::fmtflags;` 才能使用 `my_flags` 做為的類型別名 `std::ios_base::fmtflags` 。

## <a name="example-misspelled-identifier"></a>範例：拼錯的識別碼

當識別碼名稱拼錯，或識別碼使用錯誤的大寫和小寫字母時，通常就會發生此錯誤。 宣告中的名稱必須與您所使用的名稱完全相符。

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>範例：使用不限範圍的識別碼

如果您的識別碼未正確設定範圍，就會發生此錯誤。 如果您在使用時看到 C2065 `cout` ，這就是原因。 當 c + + 標準程式庫函式和運算子不是由命名空間完整限定時，或者您未使用指示詞將 `std` 命名空間帶入目前的範圍時，編譯器就找不到 **`using`** 它們。 若要修正此問題，您必須完整限定識別碼名稱，或使用指示詞來指定命名空間 **`using`** 。

這個範例無法編譯，因為 `cout` 和 `endl` 是在命名空間中定義的 `std` ：

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

在、或類型內宣告的識別碼 **`class`** ， **`struct`** **`enum class`** 也必須在您于該範圍之外使用時，以其封閉範圍的名稱來限定。

## <a name="example-precompiled-header-isnt-first"></a>範例：先行編譯標頭檔不是第一個

如果您在先行編譯標頭檔的 #include 之前放置任何預處理器指示詞（例如 #include、#define 或 #pragma），就會發生這個錯誤。 如果您的原始程式檔使用先行編譯標頭檔（也就是使用 **/yu**編譯器選項來編譯），則會忽略先行編譯標頭檔之前的所有預處理器指示詞。

這個範例無法編譯，因為 `cout` 和 `endl` 是定義在 \<iostream> 標頭中，因為它包含在先行編譯標頭檔之前，所以會被忽略。 若要建立此範例，請建立這三個檔案，然後編譯 stdafx.h，然後編譯 C2065_pch .cpp。

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

若要修正此問題，請將的 #include 新增 \<iostream> 至先行編譯標頭檔，或將它移到您的原始程式檔中包含先行編譯標頭檔之後。

## <a name="example-missing-header-file"></a>範例：遺漏標頭檔

您尚未包含宣告識別碼的標頭檔。 請確定包含識別碼宣告的檔案包含在使用它的每個原始程式檔中。

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

另一個可能的原因是您使用了初始化運算式清單，但未包含 \<initializer_list> 標頭。

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

如果您定義、或，您可能會在 Windows 傳統型應用程式來源檔案中看到此錯誤 `VC_EXTRALEAN` `WIN32_LEAN_AND_MEAN` `WIN32_EXTRA_LEAN` 。 這些預處理器宏會從 windows. h 和 afxv 中排除一些標頭檔， \_ 以加快編譯速度。 如需排除的內容的最新說明，請查看 windows. h 和 afxv_w32。

## <a name="example-missing-closing-quote"></a>範例：遺漏右引號

如果您遺漏字串常數後面的右引號，就會發生這個錯誤。 這是混淆編譯器的簡單方式。 請注意，遺漏右引號可能是報告錯誤位置之前的幾行。

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>範例：在 for 迴圈範圍外使用 iterator

如果您在迴圈中宣告反覆運算器變數 **`for`** ，然後嘗試在迴圈範圍外使用該反覆運算器變數，就會發生這個錯誤 **`for`** 。 根據預設，編譯器會啟用[/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)編譯器選項。 如需詳細資訊，請參閱[Debug Iterator 支援](../../standard-library/debug-iterator-support.md)。

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>範例：預處理器已移除宣告

如果您參考的函式或變數是有條件地編譯的程式碼，但未針對目前的設定進行編譯，就會發生這個錯誤。 如果您在您的組建環境中目前不支援的標頭檔中呼叫函式，也可能會發生這種情況。 如果某些變數或函數只有在定義特定預處理器宏時才可使用，請確定在定義相同的預處理器宏時，只能編譯呼叫這些函式的程式碼。 這個問題很容易出現在 IDE 中，因為如果未針對目前的組建設定定義必要的預處理器宏，函式的宣告會呈現灰色。

這是當您在 Debug （但不是零售）中建立時，可運作的程式碼範例：

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>範例： c + +/CLI 類型推斷失敗

如果無法從使用的參數推算預定的型別引數，則呼叫泛型函式時，就會發生這個錯誤。 如需詳細資訊，請參閱泛型函式[（c + +/cli）](../../extensions/generic-functions-cpp-cli.md)。

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>範例： c + +/CLI 屬性參數

針對 Visual Studio 2005： Visual C++ 屬性的參數檢查所執行的編譯器一致性工作，也可能產生此錯誤。

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
