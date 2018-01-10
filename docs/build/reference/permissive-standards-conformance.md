---
title: "-寬鬆-（標準一致性） |Microsoft 文件"
ms.date: 11/11/2016
ms.technology: cpp-tools
ms.topic: article
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs: C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 90ff6d2be6174f32d7d93252ebd8b693b422076d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="permissive--standards-conformance"></a>寬鬆 /-（標準的一致性）

指定給編譯器的標準一致性模式。 使用此選項可協助您找出並修正程式碼，使其更正確且更容易移植一致性問題。

## <a name="syntax"></a>語法

> **寬鬆 /-**

## <a name="remarks"></a>備註

您可以使用**/ 寬鬆-**編譯器選項以指定符合標準的編譯器行為。 此選項會停用 寬鬆的行為，並設定[/Zc](../../build/reference/zc-conformance.md)嚴格一致性的編譯器選項。 在 IDE 中，此選項也讓 IntelliSense 引擎底線不合格的程式碼。 

根據預設， **/ 寬鬆-**選項設定新建立的 Visual Studio 2017 版本 15.5 和更新版本的專案中。 根據預設，在舊版中未設定它。 當設定此選項、 編譯器會產生診斷錯誤或警告非標準的語言建構時偵測到您的程式碼中時，包括一些常見的錯誤在前置的 C + + 11 程式碼。

**/ 寬鬆-**選項適用於幾乎所有的標頭檔，從最新的 Windows 套件，例如軟體開發套件 (SDK) 或 Windows Driver Kit (WDK)，啟動 Windows 改建立者 (10.0.16299.0) SDK 中。 較舊的 sdk 版本可能無法編譯下**/ 寬鬆-**各種來源的程式碼的一致性。 編譯器和 Sdk 的出貨上不同的版本時間軸，因此有一些其餘的問題。 如需特定的標頭檔問題，請參閱[Windows 標頭問題](#windows-header-issues)下方。

**/ 寬鬆-**選項集[/zc: strictstrings](../../build/reference/zc-conformance.md)和[/zc: rvaluecast](../../build/reference/zc-conformance.md)合格行為的選項。 它們會預設為不合格的行為。 您可以傳遞特定**/Zc**後選項**/ 寬鬆-**覆寫這個行為在命令列上。

在 Visual Studio 2017 版本 15.3，一開始編譯器的版本中**/ 寬鬆-**選項集**/Zc:ternary**選項。 編譯器也會實作多個兩階段的名稱查閱的需求。 當**/ 寬鬆-**設定選項時，編譯器會剖析函式和類別識別相依及非相依名稱的範本中所使用的範本定義。 在此版本中，執行名稱相依性分析。

環境特定擴充功能和標準保留最多實作的語言區域不會受到**/ 寬鬆-**。 例如，Microsoft 專有`__declspec`，呼叫慣例和結構化例外狀況處理關鍵字，以及特定編譯器的 pragma 指示詞或屬性未標示在編譯器**/ 寬鬆-**模式。

**/ 寬鬆-**選項會使用一致性支援目前的編譯器版本以判斷哪些語言建構會不合格。 選項不會判斷是否您的程式碼是否符合特定版本的 c + + 標準。 若要啟用的最新草稿標準的所有實作的編譯器支援，請使用[/std:latest](../../build/reference/std-specify-language-standard-version.md)選項。 若要限制目前已實作 C + + 17 標準的編譯器支援，請使用[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)選項。 若要限制為更符合 C + + 14 標準的編譯器支援，請使用[/std:c + + 14](../../build/reference/std-specify-language-standard-version.md)選項，預設值。

不所有 C + + 11、 C + + 14 中或 C + + 17 標準符合在 Visual Studio 2017 Visual c + + 編譯器支援的程式碼。 **/ 寬鬆-**選項可能無法偵測出問題有關兩階段的名稱查閱的某些層面，繫結到臨時非 const 的參考、 視為直接初始化中的複本初始化，允許在多個使用者定義轉換初始化或替代的語彙基元的邏輯運算子，以及其他不受支援的一致性區域。 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="how-to-fix-your-code"></a>如何修正您的程式碼

以下是一些範例的程式碼偵測為不合格當您使用**/ 寬鬆-**，以及修正問題的建議方式。

#### <a name="use-default-as-an-identifier-in-native-code"></a>使用預設值為原生程式碼中的識別項

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>相依的基底中的查閱成員

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>使用的成員宣告中的限定名稱

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>初始化多個成員初始設定式中的等位成員

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>隱藏的 friend 名稱查閱規則

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>使用陣列界限內的限定範圍的列舉

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>針對每個原生程式碼中使用

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>使用 ATL 屬性

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be 
// used to automatically obtain a *.idl file for the interfaces with 
// annotation. Second, add a midl step to your build system to make 
// sure that the C++ interface definitions are outputted. 
// Last, adjust your existing code to use ATL directly as shown in 
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>模稜兩可的條件運算子的引數

在 Visual Studio 2017 15.3 版本之前，編譯器的版本中，編譯器會接受引數的條件運算子 （或三元運算子） `?:` ，會被視為模稜兩可的標準。 在**/ 寬鬆-**模式中，編譯器現在會發出在不進行診斷，在舊版本所編譯的情況下的一或多個診斷。

常見的情況錯誤可能會造成這項變更包括：

- 錯誤 C2593: 'operator' 嗎？ 模稜兩可

- 錯誤 C2679： 二進位 '？ ': 找不到運算子採用右方運算元類型 'B' （或沒有可接受的轉換）

- 錯誤 C2678： 二進位 '？ ': 找不到運算子採用類型為 'A' 的左方運算元 （或沒有可接受的轉換）

- 錯誤 C2446: ':': 沒有從 'B' 為 'A' 的轉換

某些類別 C 類型 t。 提供從另一個類型 T 的非明確建構函式和非明確的轉換運算子時，可能會導致此問題的一般程式碼模式在此情況下，第 2 個引數轉換成第 3 種和第 3 個引數轉換成第 2 種是有效的轉換，這是根據標準模稜兩可。

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

T 代表其中一個 null 結束的字串類型時，有是常見的模式的重要例外狀況 (比方說， `const char *`， `const char16_t *`，依此類推) 的實際引數和`?:`是字串常值對應的型別。 C + + 17 已經從 C + + 14 語意。 如此一來，範例 2 中的程式碼會接受在**/std:c + + 14**和已拒絕下**/std:c + + 17**時**/Zc:ternary**或**/permissive-**用。

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s; 
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

在具有型別的單一引數的條件運算子是另一種情況，您可能會看到錯誤`void`。 此情況下可能很常見中類似的判斷提示巨集。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您可能也會看到的範本 metaprogramming，可能會在將變更條件運算子的結果型別中的錯誤**/Zc:ternary**和**/ 寬鬆-**。 若要解決此問題是使用單向[std::remove_reference](../../standard-library/remove-reference-class.md)上產生的型別。

```cpp
// Example 4: different result types 
extern bool cond;
extern int count;
char  a = 'A'; 
const char  b = 'B'; 
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary 
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary 
```

#### <a name="two-phase-name-look-up-partial"></a>兩階段的名稱查閱 （部分）

當**/ 寬鬆-**選項設在 Visual Studio 2017 15.3 版本中，編譯器會剖析函式和類別識別相依及非相依名稱兩階段的名稱，視需要的範本中所使用的樣板定義查閱。 在此版本中，執行名稱相依性分析。 特別是，樣板定義的內容中未宣告為非相依名稱會導致診斷訊息所需的 ISO c + + 標準。 不過，需要不是引數相依查閱定義內容中的非相依名稱的繫結。

```cpp
// dependent base
struct B {
    void g();
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

### <a name="windows-header-issues"></a>Windows 標頭的問題

**/ 寬鬆-**選項是 Windows 套件，Windows 改建立者更新 SDK (10.0.16299.0) 之前, 的版本或 Windows Driver Kit (WDK) 版本 1709年過於嚴格。 我們建議您更新至最新版本的 Windows 套件，才能使用**/ 寬鬆-** Windows 或裝置驅動程式碼中。

Windows 改建立者更新 SDK (10.0.16299.0) 或 Windows Driver Kit (WDK) 1709年中的特定標頭檔仍會有問題，使它們與使用的不相容**/ 寬鬆-**。 若要解決這些問題，我們建議您限制只有那些原始程式碼檔需要它們，並將移除使用這些標頭**/ 寬鬆-**選項，當您編譯這些特定的原始程式碼檔。 下列問題專屬於 Windows 改建立者更新 SDK (10.0.16299.0):

#### <a name="issue-in-umqueryh"></a>在 um\Query.h 中的問題

當使用**/ 寬鬆-**編譯器參數，`tagRESTRICTION`結構不會編譯因為 case(RTOr) 成員 '。

```cpp
struct tagRESTRICTION
    {
    ULONG rt;
    ULONG weight;
    /* [switch_is][switch_type] */ union _URes
        {
        /* [case()] */ NODERESTRICTION ar;
        /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
        /* [case()] */ NODERESTRICTION pxr;
        /* [case()] */ VECTORRESTRICTION vr;
        /* [case()] */ NOTRESTRICTION nr;
        /* [case()] */ CONTENTRESTRICTION cr;
        /* [case()] */ NATLANGUAGERESTRICTION nlr;
        /* [case()] */ PROPERTYRESTRICTION pr;
        /* [default] */  /* Empty union arm */
        } res;
    };
```

若要解決此問題，編譯包含不含 Query.h **/ 寬鬆-**選項。

#### <a name="issue-in-umcellularapioemh"></a>在 um\cellularapi_oem.h 中的問題

當使用**/ 寬鬆-**編譯器參數、 的向前宣告`enum UICCDATASTOREACCESSMODE`會導致警告：

```cpp
typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
```

不限範圍列舉的向前宣告是 Microsoft 擴充功能。 若要解決此問題，編譯包含不含 cellularapi_oem.h **/ 寬鬆-**選項，或使用[/wd](../../build/reference/compiler-option-warning-level.md)警告 C4471 轉為無回應的選項。

#### <a name="issue-in-umomscripth"></a>在 um\omscript.h 中的問題

在 C + + 03 中，從字串常值轉換成 BSTR (即的 typedef ' wchar_t *') 是已被取代，但允許。 在 C + + 11 中，不再允許轉換。

```cpp
virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
    /* [in] */ __RPC__in BSTR propname,
    /* [in] */ __RPC__in BSTR expression,
    /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
```

若要解決此問題，編譯包含不含 omscript.h **/ 寬鬆-**選項，或使用**/Zc:strictStrings-**改為。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

在 Visual Studio 2017 版本 15.5 和更新版本中，使用此程序：

1. 開啟您的專案**屬性頁** 對話方塊。

1. 在下**組態屬性**，依序展開**C/c + +**資料夾，然後選擇 **語言**屬性頁。

1. 變更**一致性模式**屬性值設定為**是 (/ 寬鬆-)**。 選擇**確定**或**套用**以儲存變更。

在 Visual Studio 2017 版本 15.5 之前的版本中，使用此程序：

1. 開啟您的專案**屬性頁** 對話方塊。

1. 在下**組態屬性**，依序展開**C/c + +**資料夾，然後選擇 **命令列**屬性頁。

1. 輸入**/ 寬鬆-**編譯器選項在**其他選項**方塊。 選擇**確定**或**套用**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
