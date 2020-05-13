---
title: MSVC 實驗預處理器概述
description: MSVC 預處理器正在更新,以便符合 C/C++ 標準。
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337488"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC 實驗預處理器概述

::: moniker range="vs-2015"

Visual Studio 2015 使用傳統的預處理器,這不符合標準C++。 使用[/實驗前](../build/reference/experimental-preprocessor.md)處理器編譯器開關,在 Visual Studio 2017 和 Visual Studio 2019 中提供了一個實驗預處理器。 有關在 Visual Studio 2017 和 Visual Studio 2019 中使用新預處理器的詳細資訊,請造訪。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker-end

::: moniker range=">=vs-2017"

我們正在更新 Microsoft C++預處理器,以提高標準一致性、修復長期存在的 Bug 並更改一些正式未定義的行為。 我們還添加了新的診斷程式來警告宏定義中的錯誤。

這些更改可透過在 Visual Studio 2017 或 Visual Studio 2019 中使用[/實驗前處理器](../build/reference/experimental-preprocessor.md)編譯器開關。 默認預處理器行為與早期版本相同。

從 Visual Studio 2019 版本 16.5 開始,C++20 標準的實驗預處理器支援已完成。

## <a name="new-predefined-macro"></a>新的預先定義巨集

您可以檢測編譯時正在使用的預處理器。 檢查預定義的宏[\_MSVC\_傳統](predefined-macros.md)值,以判斷是否正在使用傳統的預處理器。 此宏由支援它的編譯器版本無條件設置,獨立於調用預處理器的版本。 其值對於傳統的預處理器為 1。 對於符合要求的預處理器,它是 0。

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>實驗預處理器的行為變化

實驗預處理器的初步工作重點是使所有宏擴展都符合標準。 它允許您將 MSVC 編譯器與當前被傳統行為阻止的庫一起使用。 我們在真實項目中測試了更新的預處理器。 以下是我們發現的一些更常見的突發性更改:

### <a name="macro-comments"></a>巨解

傳統的預處理器基於字元緩衝區,而不是預處理器令牌。 它允許異常行為,如以下前處理器註釋技巧,這在符合的預處理器下不起作用:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

符合標準的修復程式是在相應的`int myVal``#ifdef/#endif`指令中聲明:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L_val

傳統的預處理器錯誤地將字串前置[字串( 字串) 運算元 (#)](stringizing-operator-hash.md)運算子的結果合併:

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

在這種情況下,前置碼是`L`不必要的,因為相鄰的字串文本無論如何都在宏擴展後合併。 傳回時相容的修復程式是改變定義:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

在將參數「串」到寬字串文字的便利宏中也發現了同樣的問題:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

您可以通過多種方式解決此問題:

- 使用和`L""``#str`的字串串聯來添加首碼。 連續的字串文字在巨集延伸後合併:

   ```cpp
   #define STRING1(str) L""#str
   ```

- 使用其他巨集`#str`延伸字串化後加入前置文字

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- 使用串聯運算符`##`組合權杖。 `##`和的操作`#`順序未指定,儘管在這種情況下,所有編譯器似乎都在評估`#`運算符之前。 `##`

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>不合法警告\#\#

當[令牌粘貼運算符 (#)](token-pasting-operator-hash-hash.md)不產生單個有效的預處理令牌時,該行為未定義。 傳統的預處理器無法悄悄地組合權杖。 新的預處理器與大多數其他編譯器的行為匹配,併發出診斷。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>變異巨集的逗號

傳統的 MSVC 前處理器始終`__VA_ARGS__`在空 替換之前刪除逗號。 實驗前處理器更密切地遵循其他流行的跨平台編譯器的行為。 要刪除逗號,必須缺少可變參數(而不僅僅是空),並且必須用`##`運算符標記它。 請考慮下列範例：

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

在下面的示例中,在調用的宏中`FUNC2(1)`缺少對可變參數的調用。 在調用`FUNC2(1, )`變數參數時為空,但不丟失(請注意參數清單中的逗號)。

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

在即將出臺的C++20標準中,此問題已通過添加`__VA_OPT__`得到解決。 Visual Studio 2019 版本 16.5 中`__VA_OPT__`提供了實驗前處理器支援 。

### <a name="c20-variadic-macro-extension"></a>C++20可變宏擴展

實驗前處理器支援C++20變幻宏參數消除:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

此代碼不符合 C++20 標準。 在 MSVC 中,實驗前處理器將此C++20 行為擴展到**`/std:c++14`** 較低**`/std:c++17`** 的語言 標準模式 (,)。 此擴展與其他主要跨平臺C++編譯器的行為匹配。

### <a name="macro-arguments-are-unpacked"></a>宏參數"解壓縮"

在傳統的預處理器中,如果宏將其參數之一轉發到另一個從屬宏,則在插入參數時不會"解壓縮"。 通常,這種優化被忽視,但它可能導致異常行為:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

擴展`A()`時,傳統的預處理器將所有打包的參數`__VA_ARGS__`轉發 到TWO_STRINGS的第一個參數,從而留下`TWO_STRINGS`空的可變參數。 這將導致結果`#first`為"1,2",而不僅僅是"1"。 如果你緊隨其後,那麼您可能想知道傳統前處理器擴展的結果`#__VA_ARGS__`發生了什麼:如果變數參數為空,則應該導致一個空字串文本。 `""` 另一個問題阻止生成空字串文本權杖。

### <a name="rescanning-replacement-list-for-macros"></a>重新掃描巨集的替代清單

替換宏後,將重新掃描生成的權杖以替換其他巨集識別碼。 傳統的預處理器用於進行再掃描的演演演算法不符合,如本示例中基於實際代碼所示:

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

儘管此示例看起來有點精心設計,但我們在真實世界代碼中看到了它。 為了瞭解發生了什麼,我們可以從 以下開始分解`DO_THING`擴展 :

1. `DO_THING(1, "World")`延伸到`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`延伸到`IMPL ## 1`, 延伸到`IMPL1`
1. 現在權杖處於此狀態:`IMPL1 ECHO(("Hello", "World"))`
1. 預處理器尋找類似函數的巨集識別碼`IMPL1`。 因為它沒有後跟`(`, 它不被視為類似於函數的宏調用。
1. 預處理器將轉到以下令牌。 因為呼叫類似函數的巨集`ECHO`: `ECHO(("Hello", "World"))``("Hello", "World")`
1. `IMPL1`永遠不會再考慮擴展,因此擴展的全部結果是:`IMPL1("Hello", "World");`

要修改宏在實驗前處理器和傳統前處理器下的行為方式相同,請添加另一層間接:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>功能不完整

從 Visual Studio 2019 版本 16.5 開始,實驗預處理器功能齊全,適用於 C++20。 在 Visual Studio 的早期版本中,實驗預處理器大部分完成,儘管某些預處理器指令邏輯仍可以追溯到傳統行為。 以下是 16.5 之前 Visual Studio 版本中不完整功能的部分清單:

- 支援 `_Pragma`
- C++20 功能
- 增強阻塞錯誤:在版本 16.5 之前,預處理器常量表達式中的邏輯運算符未在新的預處理器中完全實現。 在某些`#if`指令中,新的預處理器可以回落到傳統的前處理器。 只有當與傳統預處理器不相容的宏得到擴展時,效果才會明顯。 在構建 Boost 預處理器插槽時,可能會發生這種情況。

::: moniker-end
