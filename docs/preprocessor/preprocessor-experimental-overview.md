---
title: MSVC 實驗性預處理器總覽
description: 正在更新 MSVC 預處理器以符合 C/C++標準。
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: eb861b18a8d42c73429f6d00a3f47b35c9b198ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090556"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC 實驗性預處理器總覽

::: moniker range="vs-2015"

Visual Studio 2015 使用傳統預處理器，這不符合標準C++。 您可以使用[/experimental：預處理器](../build/reference/experimental-preprocessor.md)編譯器參數，在 Visual Studio 2017 和 Visual Studio 2019 中提供實驗性預處理器。 如需在 Visual Studio 2017 和 Visual Studio 2019 中使用新預處理器的詳細資訊，請閱讀。 若要查看它，請使用檔版本選取器來選取其中一個版本。

::: moniker-end

::: moniker range=">=vs-2017"

我們正在更新 Microsoft C++預處理器，以改善標準一致性、修正長期以來非常 bug，以及變更一些已正式定義的行為。 我們也加入了新的診斷，以警告巨集定義中的錯誤。

您可以使用 Visual Studio 2017 或 Visual Studio 2019 中的[/experimental：預處理器](../build/reference/experimental-preprocessor.md)編譯器參數，來取得這些變更。 預設的預處理器行為與先前的版本相同。

從 Visual Studio 2019 16.5 版開始，c + + 20 標準的實驗性預處理器支援已完成功能。

## <a name="new-predefined-macro"></a>新增預先定義的宏

您可以在編譯時期偵測正在使用的預處理器。 檢查預先定義宏的值[\_MSVC\_傳統](predefined-macros.md)，以判斷傳統預處理器是否正在使用中。 這個宏是由支援它的編譯器版本無條件設定，獨立于叫用的預處理器。 傳統預處理器的值為1。 它是0，適用于符合規範的預處理器。

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>實驗性預處理器中的行為變更

實驗性預處理器的初始工作已著重于讓所有宏擴充都符合標準。 它可讓您使用 MSVC 編譯器，搭配目前傳統行為所封鎖的程式庫。 我們已在真實世界的專案上測試更新的預處理器。 以下是我們發現的一些較常見的重大變更：

### <a name="macro-comments"></a>宏批註

傳統預處理器是以字元緩衝區為基礎，而不是預處理器標記。 它允許不尋常的行為，例如下列預處理器批註訣竅，這在符合規範的預處理器下無法運作：

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

符合標準的修正方法是在適當的 `#ifdef/#endif` 指示詞內宣告 `int myVal`：

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # val

傳統預處理器不正確地將字串前置詞與[字串化運算子（#）](stringizing-operator-hash.md)運算子的結果結合：

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

在此情況下，`L` 前置詞是不必要的，因為連續的字串常值會在宏展開之後合併。 與舊版相容的修正程式是變更定義：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

同樣的問題也可以在方便性宏中找到，也就是「字串化」寬字元串常值的引數：

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

您可以透過各種方式來修正此問題：

- 使用 `L""` 和 `#str` 的字串串連來加入前置詞。 連續的字串常值會在宏展開之後合併：

   ```cpp
   #define STRING1(str) L""#str
   ```

- 使用其他宏展開來 stringized `#str` 之後，新增前置詞

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- 使用串連運算子 `##` 來結合權杖。 `##` 和 `#` 的作業順序並未指定，但在此情況下，所有編譯器似乎都會評估 `#` `##` 運算子。

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>\#不正確 \# 警告

當[標記貼入的運算子（# #）](token-pasting-operator-hash-hash.md)不會產生單一有效的前置處理 token 時，此行為是未定義的。 傳統預處理器會以無訊息模式合併標記。 新的預處理器會符合大部分其他編譯器的行為，併發出診斷。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Variadic 宏中的逗點 elision

傳統的 MSVC 預處理器一律會在空白 `__VA_ARGS__` 取代之前移除逗號。 實驗性預處理器會更密切遵循其他熱門跨平臺編譯器的行為。 若要移除逗號，variadic 引數必須遺失（不只是空白），而且必須以 `##` 運算子標記。 請考慮下列範例：

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

在下列範例中，在所叫用的宏中遺漏 variadic 引數 `FUNC2(1)` 的呼叫。 在 `FUNC2(1, )` 的呼叫中，variadic 引數是空的，但不會遺失（請注意引數清單中的逗號）。

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

在未來的 c + + 20 標準中，已藉由新增 `__VA_OPT__`來解決此問題。 從 Visual Studio 2019 16.5 版開始，提供 `__VA_OPT__` 的實驗性預處理器支援。

### <a name="c20-variadic-macro-extension"></a>C + + 20 variadic 宏擴充功能

實驗性預處理器支援 c + + 20 variadic 宏引數 elision：

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

此程式碼在 c + + 20 標準之前不符合規範。 在 MSVC 中，實驗性預處理器會將此 c + + 20 行為延伸至較低的語言標準模式（ **`/std:c++14`** 、 **`/std:c++17`** ）。 此延伸模組符合其他主要跨平臺C++編譯器的行為。

### <a name="macro-arguments-are-unpacked"></a>宏引數為「已解壓縮」

在傳統預處理器中，如果宏將它的其中一個引數轉送至另一個相依宏，則引數在插入時不會出現「已解壓縮」。 此優化通常會被忽略，但可能會導致異常的行為：

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

當擴充 `A()`時，傳統預處理器會將 `__VA_ARGS__` 封裝的所有引數轉送至 TWO_STRINGS 的第一個引數，這會保留 `TWO_STRINGS` 空白的 variadic 引數。 這會導致 `#first` 的結果為 "1，2" 而不只是 "1"。 如果您密切關注，那麼您可能會想知道傳統預處理器擴充中 `#__VA_ARGS__` 的結果發生了什麼事：如果 variadic 參數是空的，它應該會導致空的字串常值 `""`。 個別的問題會保留產生的空字串常值 token。

### <a name="rescanning-replacement-list-for-macros"></a>重新掃描宏的取代清單

取代宏之後，會重新掃描產生的權杖，以取代其他宏識別碼。 傳統預處理器執行重新掃描所使用的演算法不符合，如下列範例所示，以實際程式碼為基礎：

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

雖然此範例看起來有點假設，但我們已在實際程式碼中看到它。 若要查看發生的狀況，我們可以從 `DO_THING`開始細分擴充：

1. `DO_THING(1, "World")` 擴充至 `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` 展開為 `IMPL ## 1`，它會展開至 `IMPL1`
1. 現在，權杖處於此狀態： `IMPL1 ECHO(("Hello", "World"))`
1. 預處理器會尋找類似函數的宏識別碼 `IMPL1`。 由於後面沒有 `(`，因此不會被視為類似函式的宏調用。
1. 預處理器會移至下列權杖。 它會尋找會叫用類似函式的宏 `ECHO`： `ECHO(("Hello", "World"))`，它會展開至 `("Hello", "World")`
1. `IMPL1` 永遠不會被視為展開，因此擴充的完整結果為： `IMPL1("Hello", "World");`

若要修改宏，使其在實驗性預處理器和傳統預處理器中的行為方式相同，請新增另一層間接取值：

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

## <a name="incomplete-features"></a>不完整的功能

從 Visual Studio 2019 16.5 版開始，實驗性預處理器是 c + + 20 的功能完整。 在舊版的 Visual Studio 中，實驗性預處理器大部分都是完整的，雖然某些預處理器指示詞邏輯仍然會回到傳統的行為。 以下是16.5 之前 Visual Studio 版本中未完成功能的部分清單：

- 支援 `_Pragma`
- C + + 20 功能
- 提升封鎖 bug：預處理器常數運算式中的邏輯運算子在16.5 版之前，不會在新的預處理器中完全實作為。 在某些 `#if` 指示詞上，新的預處理器可以切換回傳統的預處理器。 只有當宏與傳統預處理器不相容時，才會有明顯的影響。 建立加速預處理器位置時，可能會發生此問題。

::: moniker-end
