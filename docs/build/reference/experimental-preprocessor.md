---
title: '/experimental: 預處理器 (啟用預處理器一致性模式)'
description: '使用/experimental: 預處理器編譯器選項, 針對標準符合的預處理器啟用實驗性編譯器支援。'
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294435"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental: 預處理器 (啟用預處理器一致性模式)

此選項可啟用符合 c + + 11 標準 (包括 C99 預處理器功能) 的實驗性權杖型預處理器。

## <a name="syntax"></a>語法

> **/experimental: 預處理器**[ **-** ]

## <a name="remarks"></a>備註

使用 **/experimental: 預處理器**編譯器選項來啟用實驗性符合的預處理器。 您可以使用 **/experimental: 預處理器-** 選項來明確指定傳統預處理器。

從 Visual Studio 2017 版15.8 開始, 可以使用 **/experimental: 預處理器**選項。

您可以在編譯時期偵測正在使用的預處理器。 檢查預先定義的宏[ \_MSVC\_](../../preprocessor/predefined-macros.md)的值, 以判斷傳統預處理器是否正在使用中。 這個宏是由支援它的編譯器版本無條件設定, 獨立于叫用的預處理器。 傳統預處理器的值為1。 對於符合標準的實驗性預處理器而言, 這是 0:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>實驗性預處理器中的行為變更

以下是啟用預處理器一致性模式時, 所發現的一些較常見的重大變更:

#### <a name="macro-comments"></a>宏批註

傳統預處理器會使用字元緩衝區, 而不是預處理器標記。 這允許一些不尋常的行為, 例如這個預處理器批註訣竅, 這在符合規範的預處理器下無法運作:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>字串前置詞 (L # val)

傳統預處理器不正確地將字串前置詞與[字串化運算子 (#)](../../preprocessor/stringizing-operator-hash.md)的結果結合:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

此處不需要前置詞, 因為連續的字串常值仍會在宏展開之後合併。 `L` 回溯相容的修正程式是將定義變更為:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

這個問題也可以在方便的宏中找到, 其中 ' 字串化 ' 寬字元串常值的引數:

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>不正確警告 ##

當[標記貼入的運算子 (# #)](../../preprocessor/token-pasting-operator-hash-hash.md)不會產生單一有效的前置處理 token 時, 此行為是未定義的。 傳統預處理器會以無訊息模式合併標記。 新的預處理器會符合大部分其他編譯器的行為, 併發出診斷。

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>Variadic 宏中的逗點 elision

參考下列範例：

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

所有主要編譯器都有一個預處理器延伸模組, 可協助解決此問題。 傳統的 MSVC 預處理器一律會在空`__VA_ARGS__`的取代之前移除逗號。 更新的預處理器會更密切遵循其他熱門跨平臺編譯器的行為。 若要移除逗號, variadic 引數必須遺失, 而不只是空的, 而且必須以`##`運算子標記:

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

在即將推出的 C + + 2a standard 中, 已藉由新增`__VA_OPT__`尚未實行的來解決此問題。

#### <a name="macro-arguments-are-unpacked"></a>宏引數為 ' 解壓縮 '

在傳統預處理器中, 如果宏將它的其中一個引數轉送至另一個相依宏, 則引數在替代時不會被「解壓縮」。 此優化通常會被忽略, 但可能會導致異常的行為:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)

const char* c[2] = { A(1, 2) };
// Conformant preprocessor results:
// const char c[2] = { "1", "2" };
// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

展開`A()`時, 傳統預處理器會將封裝在中`__VA_ARGS__`的所有引數轉送`TWO_STRINGS`至的第一個引數。 的 variadic 引數`TWO_STRINGS`是空的, 它會導致的`#first`結果`"1, 2"`不是只`"1"`是。 您可能想知道傳統預處理器擴充的結果`#__VA_ARGS__`發生了什麼事。 如果 variadic 參數是空的, 它應該會產生空字串常值 ""。 因為有不同的問題, 所以不會產生空字串常值 token。

#### <a name="rescanning-replacement-list-for-macros"></a>重新掃描宏的取代清單

取代宏之後, 會重新掃描產生的權杖, 以取代其他宏識別碼。 傳統預處理器所使用的重新掃描演算法不符合標準, 如下列範例中的實際程式碼所示:

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
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

若要查看此範例中的情況, 我們會從開始`DO_THING`細分擴充:

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

第二, CAT 已擴充:

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

這會讓權杖進入此狀態:

`IMPL1 ECHO(("Hello", "World"))`

預處理器會尋找類似函式的宏`IMPL1`識別碼, 但後面不接 "(", 因此不會被視為類似函式的宏調用。 它會移至下列權杖, 並尋找已叫用函式`ECHO`的宏:

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`不會再次考慮進行擴充, 因此擴充的完整結果為:

`IMPL1("Hello", "World");`

您可以修改宏, 使其在實驗性預處理器和傳統預處理器中的行為方式相同。 解決方法是新增另一層間接取值:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>一致性模式一致性

實驗性預處理器尚未完成, 而且某些預處理器指示詞邏輯仍然會回到傳統行為。 以下是未完成功能的部分清單:

- 支援`_Pragma`
- C + + 20 功能
- 其他診斷改良功能
- 切換以控制/E 和/P 底下的輸出
- 提高封鎖 bug:預處理器常數運算式中的邏輯運算子不會在新的預處理器中完全實作為。 在某些`#if`指示詞上, 新的預處理器可以切換回傳統的預處理器。 只有當與傳統預處理器不相容的宏展開時, 才會有明顯的效果, 這可能會在建立加速預處理器位置時發生。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/experimental: 預處理器**, 然後選擇 **[確定]** 。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
