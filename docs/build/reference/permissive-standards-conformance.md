---
title: /permissive--（標準一致性）
ms.date: 03/08/2019
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 05089ef4f0a516f932d82f13be979da572701ae2
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424127"
---
# <a name="permissive--standards-conformance"></a>/permissive--（標準一致性）

指定給編譯器的標準一致性模式。 使用此選項可協助您找出並修正在您的程式碼，使其更正確和可攜性的一致性問題。

## <a name="syntax"></a>語法

> **/permissive-**

## <a name="remarks"></a>備註

在 Visual Studio 2017 和更新版本支援此選項。

您可以使用 **/permissive--** 編譯器選項以指定且符合標準的編譯器行為。 此選項會停用 寬鬆的行為，並設定[/Zc](zc-conformance.md)嚴格相容性的編譯器選項。 在 IDE 中，這個選項也會讓 IntelliSense 引擎底線不合格的程式碼。

根據預設， **/permissive--** 選項設定新建立的 Visual Studio 2017 15.5 版和更新版本的專案中。 它不是在舊版的預設設定。 當設定此選項、 編譯器會產生診斷錯誤或警告非標準語言建構時偵測到您的程式碼中時，包括一些常見的錯誤，在前置-C + + 11 程式碼。

**/Permissive--** 選項適用於幾乎所有的標頭檔，從最新的 Windows 套件，例如軟體開發套件 (SDK) 或 Windows Driver Kit (WDK)，以 Windows Fall Creators SDK (10.0.16299.0) 啟動。 較舊版本的 SDK 可能無法編譯底下 **/permissive--** 各種來源的程式碼合規性原因。 編譯器和 Sdk 的出貨上不同的版本時間軸，因此有一些剩餘問題。 如需特定的標頭檔問題，請參閱[Windows 標頭問題](#windows-header-issues)如下。

**/Permissive--** 選項組[/zc: referencebinding](zc-referencebinding-enforce-reference-binding-rules.md)， [/zc: strictstrings](zc-strictstrings-disable-string-literal-type-conversion.md)，以及[/zc: rvaluecast](zc-rvaluecast-enforce-type-conversion-rules.md)選項，以符合行為。 這些選項預設值，不符合標準的行為。 您可以傳遞特定 **/Zc**後選項 **/permissive--** 覆寫這個行為在命令列上。

在 Visual Studio 2017 15.3 版中，編譯器開始的版本中 **/permissive--** 選項組[/zc: ternary](zc-ternary.md)選項。 編譯器也會實作多個兩階段名稱查閱的需求。 當 **/permissive--** 設定選項時，編譯器會剖析函式和類別樣板定義，並會識別用於範本的相依和非相依名稱。 在此版本中，會執行名稱相依性分析。

環境特定擴充功能和標準保留最多實作的語言區域不會受到 **/permissive--**。 例如，Microsoft 專有`__declspec`，呼叫慣例和結構化例外狀況處理關鍵字和特定編譯器的 pragma 指示詞或屬性未標示在編譯器 **/permissive--** 模式。

**/Permissive--** 選項會使用一致性支援目前的編譯器版本以判斷哪些語言建構會不合格。 此選項不會判斷您的程式碼是否符合特定版本的C++標準。 若要啟用之最新草稿標準的所有實作的編譯器支援，請使用[/std:latest](std-specify-language-standard-version.md)選項。 若要限制目前已實作 c++17 標準的編譯器支援，請使用[/std: c + + 17](std-specify-language-standard-version.md)選項。 若要限制為更符合 C + + 14 標準的編譯器支援，請使用[/std: c + + 14](std-specify-language-standard-version.md)選項，這是預設值。

不所有 C + + 11、 C + + 14 或 C + + 17 標準符合所有版本的 Visual Studio 2017 中的 MSVC 編譯器支援程式碼。 根據 Visual Studio 版本而定 **/permissive--** 選項可能無法偵測出關於兩階段名稱查閱的某些層面、 繫結到暫存非 const 的參考、 複製 init 視為直接 init、 允許的問題多個使用者定義轉換在初始化或替代語彙基元中的邏輯運算子，以及其他不受支援的一致性區域。 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 若要取得充分利用 **/permissive--**，更新為最新版本的 Visual Studio。

### <a name="how-to-fix-your-code"></a>如何修正您的程式碼

以下是一些被偵測為不合格時您所使用的程式碼範例 **/permissive--**，以及修正問題的建議方式。

#### <a name="use-default-as-an-identifier-in-native-code"></a>使用預設值為原生程式碼中的識別項

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>查閱中相依的基底成員

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>使用的成員宣告的限定名稱

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>初始化成員初始設定式中的多個等位成員

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

在 Visual Studio 2017 15.3 版之前，編譯器的版本中，編譯器會接受引數的條件運算子 （或三元運算子） `?:` ，會被視為模稜兩可由標準。 在  **/permissive--** 模式中，編譯器現在會發出一或多個診斷的情況下，不進行診斷，在舊版本中編譯。

這項變更可能會造成的常見錯誤包括：

- 錯誤 C2593: 'operator' 嗎？ 模稜兩可

- 錯誤 C2679： 二進位 '？ ': 找不到運算子接受 'B' 類型的右運算元 （或沒有可接受的轉換）

- 錯誤 C2678： 二進位 '？ ': 找不到運算子接受左方運算元類型 'A' （或沒有可接受的轉換）

- 錯誤 C2446: ':': 沒有從 'B' 為 'A' 的轉換

某些類別 C 類型 t 提供從另一個類型 T 的非明確建構函式和非明確的轉換運算子時，可能會導致此問題的典型程式碼模式在此情況下，第三個引數的型別轉換的第二個引數和第三個引數的第二個引數的型別轉換是有效的轉換。 兩者都是有效的因為它是根據標準模稜兩可。

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

沒有此一常見模式的重要例外狀況時 T 代表其中一個 null 結束的字串類型 (比方說， `const char *`，`const char16_t *`等等) 的實際引數和`?:`是一個字串對應之類型的常值。 C + + 17 已從 C + + 14 語意。 如此一來，範例 2 中的程式碼會接受下 **/std: c + + 14**和已拒絕下 **/std: c + + 17**時 **/zc: ternary**或 **/permissive-** 會使用。

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

另一種情況，您可能會在此看到錯誤是在具有型別的單一引數的條件式運算子`void`。 此情況下可能有共同的判斷提示式的巨集的。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您也可能會看到的範本中繼程式設計，可能會在將變更條件運算子的結果型別中的錯誤 **/zc: ternary**並 **/permissive--**。 若要解決此問題是使用單向[std::remove_reference](../../standard-library/remove-reference-class.md)上產生的型別。

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>兩階段名稱查閱

當 **/permissive--** 設定選項，編譯器會剖析函式和類別樣板定義，用來識別相依和非相依名稱用於兩階段名稱查閱所需的範本。 在 Visual Studio 2017 15.3 版，被執行名稱的相依性分析。 特別的是，未在範本定義的內容中宣告的非相依名稱會造成診斷訊息所需的 ISOC++標準。 在 Visual Studio 2017 15.7 版，也會完成要求定義內容中的引數相依查閱的非相依名稱的繫結。

```cpp
// dependent base
struct B {
    void g() {}
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

如果您想要舊版的行為，兩階段查閱而言，但想 **/permissive--** 行為，加入 **/zc: twophase-** 選項。

### <a name="windows-header-issues"></a>Windows 標頭的問題

**/Permissive--** 選項是太過嚴苛的 Windows 套件，Windows Fall Creators Update SDK (10.0.16299.0) 之前, 的版本或 Windows Driver Kit (WDK) 版本 1709年。 我們建議您更新至最新版本的 Windows 套件，才能使用 **/permissive--** Windows 或裝置驅動程式程式碼中。

在 2018 Update SDK (10.0.17134.0)、 Windows Fall Creators Update SDK (10.0.16299.0) 或 Windows Driver Kit (WDK) 1709年的 Windows 年 4 月中特定標頭檔仍會有問題，使它們與使用的不相容 **/permissive-**. 若要解決這些問題，我們建議您限制只有這些原始程式碼檔案需要它們，並將移除使用這些標頭 **/permissive--** 選項，當您編譯這些特定的原始程式碼檔。

這些發行的 WinRT WRL 標頭中的 Windows 2018 年 4 月 Update SDK (10.0.17134.0) 不是使用全新 **/permissive--**。 若要解決這些問題，請不要使用 **/permissive--**，或使用 **/permissive--** 具有 **/zc: twophase-** 時使用這些標頭：

- Winrt/wrl/async.h 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Winrt/wrl/implements.h 的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

這些發行的使用者模式標頭中的 Windows 2018 年 4 月 Update SDK (10.0.17134.0) 不是使用全新 **/permissive--**。 若要解決這些問題，請勿使用 **/permissive--** 時使用這些標頭：

- Um/Tune.h 中的問題

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Um/spddkhlp.h 的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco.h 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

這些問題專屬於 Windows Fall Creators Update SDK (10.0.16299.0) 中的使用者模式標頭：

- Um/Query.h 的問題

   使用時 **/permissive--** 編譯器參數`tagRESTRICTION`不會編譯結構，這是因為 case(RTOr) 成員 '。

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

   若要解決此問題，編譯檔案，包括不含 Query.h **/permissive--** 選項。

- Um/cellularapi_oem.h 的問題

   使用時 **/permissive--** 編譯器參數、 的向前宣告`enum UICCDATASTOREACCESSMODE`會產生警告：

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   不限範圍列舉的向前宣告是 Microsoft 擴充功能。 若要解決此問題，編譯檔案，包括不含 cellularapi_oem.h **/permissive--** 選項，或使用[/wd](compiler-option-warning-level.md) play C4471 警告的選項。

- Um/omscript.h 的問題

   在 c++03 中，從字串常值轉換成 BSTR (也就是 typedef ' wchar_t *') 是已被取代，但允許。 在 C + + 11 中，不再允許轉換。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   若要解決此問題，編譯檔案，包括不含 omscript.h **/permissive--** 選項，或使用 **/Zc:strictStrings-** 改。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

在 Visual Studio 2017 15.5 版和更新版本中，使用此程序：

1. 開啟您的專案**屬性頁** 對話方塊。

1. 選取 **組態屬性** > **C /C++** > **語言**屬性頁。

1. 變更**一致性模式**屬性值，以 **[是] (/permissive--)**。 選擇 **[確定]** 或是**套用**以儲存變更。

在 Visual Studio 2017 15.5 版之前的版本，使用此程序：

1. 開啟您的專案**屬性頁** 對話方塊。

1. 選取 **組態屬性** > **C /C++** > **命令列**屬性頁。

1. 請輸入 **/permissive--** 中的編譯器選項**其他選項** 方塊中。 選擇 **[確定]** 或是**套用**以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
