---
title: MSVC 新的預處理器總覽
description: 正在更新 MSVC 預處理器以符合 C/c + + 標準。
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor, experimental
- preprocessor, new
ms.openlocfilehash: c95f923d8c38250958e26431b61a71a1e6a7fdda
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041363"
---
# <a name="msvc-new-preprocessor-overview"></a>MSVC 新的預處理器總覽

::: moniker range="vs-2015"

Visual Studio 2015 使用傳統的預處理器，其不符合標準 c + + 或 C99。 從 Visual Studio 2019 16.5 版開始，c + + 20 標準的新預處理器支援已完成功能。 您可以使用 [/zc：預處理器](../build/reference/zc-preprocessor.md) 編譯器參數來取得這些變更。 從 Visual Studio 2017 15.8 版和更新版本開始，可以使用 [/experimental：預處理器](../build/reference/experimental-preprocessor.md) 編譯器參數，來取得新預處理器的實驗性版本。 如需在 Visual Studio 2017 和 Visual Studio 2019 中使用新預處理器的詳細資訊，請使用。 若要查看您慣用 Visual Studio 版本的檔，請使用 **版本** 選擇器控制項。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end

::: moniker range=">=vs-2017"

我們正在更新 Microsoft c + + 預處理器，以改善標準一致性、修正長期以來非常錯誤，以及變更某些正式定義的行為。 我們也加入了新的診斷，以警告巨集定義的錯誤。

從 Visual Studio 2019 16.5 版開始，c + + 20 標準的預處理器支援已完成功能。 您可以使用 [/zc：預處理器](../build/reference/zc-preprocessor.md) 編譯器參數來取得這些變更。 從 Visual Studio 2017 15.8 版開始，可以在舊版中使用新預處理器的實驗性版本。 您可以使用 [/experimental：預處理器](../build/reference/experimental-preprocessor.md) 編譯器參數來啟用它。 預設的預處理器行為維持與舊版相同。

## <a name="new-predefined-macro"></a>新增預先定義的宏

您可以在編譯時期偵測正在使用的預處理器。 檢查預先定義宏的值 [`_MSVC_TRADITIONAL`](predefined-macros.md) ，以判斷傳統預處理器是否正在使用中。 這個宏是由支援的編譯器版本無條件設定，與叫用預處理器無關。 傳統預處理器的值為1。 適用于符合預處理器的是0。

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-new-preprocessor"></a>新預處理器的行為變更

新預處理器的初始工作著重于讓所有宏展開都符合標準。 它可讓您搭配使用 MSVC 編譯器與傳統行為目前封鎖的程式庫。 我們在實際的專案上測試了更新的預處理器。 以下是我們發現的一些較常見的重大變更：

### <a name="macro-comments"></a>宏批註

傳統預處理器是以字元緩衝區為基礎，而不是預處理器標記。 它可允許不尋常的行為，例如下列預處理器批註技巧，此動作無法在符合規範的預處理器下運作：

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

符合標準的修正方法是在 `int myVal` 適當的指示詞內宣告 `#ifdef/#endif` ：

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # val

傳統預處理器會錯誤地將字串前置詞與字串化運算子的結果結合 [ ( # ) ](stringizing-operator-hash.md) 運算子：

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

在此情況下，不 `L` 需要前置詞，因為連續的字串常值仍會在宏展開之後合併。 回溯相容性修正是變更定義：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

同樣的問題也會出現在方便的宏中，也就是將引數「字串化」到寬字元串常值：

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

您可以透過各種方式來修正此問題：

- 使用與的字串 `L""` 串連 `#str` 來加入前置詞。 連續的字串常值會在宏展開之後組合：

   ```cpp
   #define STRING1(str) L""#str
   ```

- `#str`使用額外的宏展開在 stringized 之後新增前置詞

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- 使用串連運算子 `##` 來合併標記。 和的作業順序 `##` `#` 並未指定，但 `#` `##` 在此情況下，所有編譯器似乎都要評估運算子。

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>不正確警告 \#\#

當標記貼上的 [運算子 ( # # ) ](token-pasting-operator-hash-hash.md) 不會產生單一有效的前置處理 token 時，行為會是未定義的。 傳統預處理器不會以無訊息方式合併標記。 新的預處理器符合大部分其他編譯器的行為，併發出診斷。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Variadic 宏中的逗號省略

傳統的 MSVC 預處理器一律會在空白取代之前移除逗號 `__VA_ARGS__` 。 新的預處理器更緊密遵循其他熱門跨平臺編譯器的行為。 若要移除逗號，必須將 variadic 引數遺漏 (不能只是空的) ，而且必須使用運算子來標記 `##` 。 請考慮下列範例：

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

在下列範例中，在叫用的 `FUNC2(1)` 宏中缺少 variadic 引數的呼叫。 在 `FUNC2(1, )` variadic 引數的呼叫中是空的，但不會遺漏 (請注意引數清單中的逗號) 。

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

在即將推出的 c + + 20 標準中，已透過新增來解決此問題 `__VA_OPT__` 。 `__VA_OPT__`從 Visual Studio 2019 16.5 版開始，提供的新預處理器支援。

### <a name="c20-variadic-macro-extension"></a>C + + 20 variadic 宏延伸模組

新的預處理器支援 c + + 20 variadic 宏引數省略：

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

這段程式碼在 c + + 20 標準之前不符合規範。 在 MSVC 中，新的預處理器會將這個 c + + 20 行為延伸至較低的語言標準模式 (**`/std:c++14`** ， **`/std:c++17`**) 。 此延伸模組符合其他主要跨平臺 c + + 編譯器的行為。

### <a name="macro-arguments-are-unpacked"></a>宏引數為「已解壓縮」

在傳統的預處理器中，如果宏將它的其中一個引數轉送到另一個相依宏，則引數插入時就不會被「解壓縮」。 這種優化通常不會被忽略，但可能導致不尋常的行為：

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

展開時 `A()` ，傳統預處理器會將所有封裝的引數轉送 `__VA_ARGS__` 至 TWO_STRINGS 的第一個引數，而將 variadic 引數保留 `TWO_STRINGS` 為空白。 這會導致的結果 `#first` 是 "1，2" 而不只是 "1"。 如果您要密切關注，您可能會想知道傳統預處理器擴充的結果會發生什麼事 `#__VA_ARGS__` ：如果 variadic 參數是空的，則它應該會產生空的字串常值 `""` 。 不同的問題會導致產生空白字串常值標記。

### <a name="rescanning-replacement-list-for-macros"></a>重新掃描宏的取代清單

取代宏之後，會重新掃描產生的權杖，以取代其他宏識別碼。 傳統預處理器用來執行重新掃描的演算法不符合規範，如這個範例中的實際程式碼所示：

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

雖然此範例看起來有點假設，但我們已在現實世界的程式碼中看到它。

若要查看發生了什麼事，我們可以從以下開始細分擴充 `DO_THING` ：

1. `DO_THING(1, "World")` 展開至 `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` 展開至 `IMPL ## 1` ，展開至 `IMPL1`
1. 現在權杖會處於此狀態： `IMPL1 ECHO(("Hello", "World"))`
1. 預處理器會尋找類似函數的宏識別碼 `IMPL1` 。 由於其後不是，因此不 `(` 會被視為類似函式的宏調用。
1. 預處理器會移至下列權杖。 它會尋找叫用類似函式的宏 `ECHO` ： `ECHO(("Hello", "World"))` ，該宏會展開為 `("Hello", "World")`
1. `IMPL1` 永遠不會再次考慮進行擴充，因此擴充的完整結果為： `IMPL1("Hello", "World");`

若要在新的預處理器和傳統預處理器下修改宏的行為方式，請新增另一個間接取值層：

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

## <a name="incomplete-features-before-165"></a>16.5 之前的未完成功能

從 Visual Studio 2019 16.5 版開始，新的預處理器是 c + + 20 的完整功能。 在舊版的 Visual Studio 中，新的預處理器大多是完整的，雖然某些預處理器指示詞邏輯仍會恢復為傳統行為。 以下是16.5 之前 Visual Studio 版本中未完成功能的部分清單：

- 支援 `_Pragma`
- C + + 20 功能
- 提高封鎖 bug：預處理器常數運算式中的邏輯運算子不會在16.5 版之前的新預處理器中完整實作為。 在某些指示詞上 `#if` ，新的預處理器可以切換回傳統的預處理器。 只有當宏與傳統預處理器的擴充功能不相容時，效果才會很明顯。 建立加速預處理器位置時，可能會發生此問題。

::: moniker-end
