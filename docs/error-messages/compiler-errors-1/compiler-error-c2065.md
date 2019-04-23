---
title: 編譯器錯誤 C2065
ms.date: 09/01/2017
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 3daf2cd532cd07225b822c80b46fc28274d4e2a8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779397"
---
# <a name="compiler-error-c2065"></a>編譯器錯誤 C2065

> '*識別碼*': 未宣告的識別項

編譯器找不到識別項的宣告。 有許多可能的原因造成此錯誤。 C2065 的最常見原因是，沒有已宣告的識別項、 識別項的拼字錯誤、 宣告的識別項的位置標頭不會包含在檔案中，或識別項遺漏範圍限定詞，比方說，`cout`而不是`std::cout`. 如需有關中宣告C++，請參閱[宣告和定義 (C++)](../../cpp/declarations-and-definitions-cpp.md)。

以下是更詳細的一些常見問題和解決方案。

## <a name="the-identifier-is-undeclared"></a>識別項未宣告

如果識別碼的變數或函式名稱，您必須宣告它，才能使用。 函式宣告也必須包含其參數型別，才能使用此函式。 如果變數使用宣告`auto`，編譯器必須能夠推斷其初始設定式的類型。

如果識別項是類別或結構中的成員或命名空間中宣告，就必須加以限定的類別或結構的名稱，或命名空間名稱，當結構、 類別或命名空間範圍外使用。 命名空間必須帶入範圍反而`using`指示詞，例如`using namespace std;`，或成員名稱必須帶入範圍`using`宣告，例如`using std::string;`。 否則，不合格的名稱被視為目前範圍中宣告的識別項。

如果識別項的標記是使用者定義型別，例如`class`或`struct`，才可以使用，必須先宣告的標記類型。 例如，宣告`struct SomeStruct { /*...*/ };`之前，您可以將變數宣告必須存在於`SomeStruct myStruct;`程式碼中。

類型別名識別項時，必須使用宣告型別`using`宣告或`typedef`才可使用。 例如，您必須宣告`using my_flags = std::ios_base::fmtflags;`您可以使用之前`my_flags`做為類型別名`std::ios_base::fmtflags`。

## <a name="example-misspelled-identifier"></a>範例： 拼字錯誤的識別碼

識別項名稱的拼字錯誤，或識別項使用錯誤的大寫和小寫字母時，通常就會發生此錯誤。 在宣告中的名稱必須完全符合您所使用的名稱。

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

## <a name="example-use-an-unscoped-identifier"></a>範例： 使用不限範圍的識別項

如果您的識別項的範圍不正確，就會發生此錯誤。 如果您使用時，您會看到 C2065 `cout`，這是原因。 當C++標準程式庫函式和運算子不會完整限定的命名空間，或不帶`std`目前的範圍內使用的命名空間`using`指示詞，編譯器找不到它們。 若要修正此問題，您必須完整限定的識別項名稱，或指定命名空間與`using`指示詞。

此範例無法編譯，因為`cout`並`endl`中所定義`std`命名空間：

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

在宣告的識別項`class`， `struct`，或`enum class`類型必須也由其封閉範圍名稱所限定，使用該範圍外時。

## <a name="example-precompiled-header-isnt-first"></a>先行編譯標頭無法第一個範例：

如果您將任何前置處理器指示詞，例如，可能會發生此錯誤 #include，#define，或 #pragma 之前, #include 的先行編譯標頭檔。 如果原始程式檔使用的先行編譯標頭檔 (亦即，如果它藉由編譯 **/Yu**編譯器選項) 會忽略之前先行編譯標頭檔的所有前置處理器指示詞。

此範例無法編譯，因為`cout`並`endl`中所定義\<iostream > 標頭，因為它會包含先行編譯標頭檔會被忽略。 若要建置此範例中，建立所有的三個檔案，然後編譯 stdafx.cpp，然後編譯 C2065_pch.cpp。

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
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

若要修正此問題，請加入 #include \<iostream > 到先行編譯標頭檔或移動後的先行編譯標頭檔包含在原始程式檔。

## <a name="example-missing-header-file"></a>範例： 遺漏標頭檔

您不包含標頭檔宣告的識別項。 請確定檔案，其中包含識別項的宣告包含每個使用它的原始程式檔中。

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

另一個可能的原因是如果您使用初始設定式清單不含\<initializer_list > 標頭。

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

如果您定義，您可能會看到此錯誤在 Windows 桌面應用程式原始程式檔`VC_EXTRALEAN`， `WIN32_LEAN_AND_MEAN`，或`WIN32_EXTRA_LEAN`。 這些前置處理器巨集排除某些標頭檔從 windows.h 和 afxv\_w32.h 以加速編譯。 尋找在 windows.h 和 afxv_w32.h 所排除的最新描述。

## <a name="example-missing-closing-quote"></a>範例： 遺漏右引號

如果您遺漏右引號字串常數之後，就會發生此錯誤。 這是容易混淆編譯器。 請注意遺漏右引號可能報告的錯誤位置之前的幾行。

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>範例： 使用 for 迴圈範圍之外的迭代器

如果您宣告中的迭代器變數，會發生此錯誤`for`迴圈，然後嘗試使用該 iterator 變數的範圍外`for`迴圈。 可讓編譯器[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)預設編譯器選項。 請參閱[偵錯迭代器支援](../../standard-library/debug-iterator-support.md)如需詳細資訊。

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

## <a name="example-preprocessor-removed-declaration"></a>範例： 前置處理器移除的宣告

如果您參考的函式或變數，就不會編譯您的目前組態的有條件地編譯程式碼中，會發生此錯誤。 如果您目前不支援在您的建置環境中的標頭檔中呼叫函式時，這也會發生。 如果特定的變數或函式時才可用在定義特定的前置處理器巨集，，請確定在定義相同的前置處理器巨集時，可以只編譯呼叫這些函式的程式碼。 此問題很容易在 IDE 中，找出的因為如果未定義必要的前置處理器巨集則為目前的組建組態，灰色函式的宣告。

這是當您建置在偵錯，但不是零售的運作方式的程式碼範例：

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

## <a name="example-ccli-type-deduction-failure"></a>範例：C++/ CLI 型別推斷失敗

如果預期的類型引數無法推算所使用的參數，當呼叫泛型函式，可以發生此錯誤。 如需詳細資訊，請參閱 <<c0> [ 泛型函式 (C++/CLI)](../../extensions/generic-functions-cpp-cli.md)。</c0>

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

## <a name="example-ccli-attribute-parameters"></a>範例：C++/ CLI 屬性參數

針對 Visual C++ 2005 所進行的編譯器一致性工作，也可能會導致這個錯誤：Visual C++ 屬性的參數檢查。

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
