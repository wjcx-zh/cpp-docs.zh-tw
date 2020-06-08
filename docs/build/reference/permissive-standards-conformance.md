---
title: /permissive- (標準一致性)
description: Microsoft c + +/permissive-（標準一致性）編譯器選項的參考指南。
ms.date: 06/04/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 3b5ddc4b4e9b70b2191a17d2201a441603182149
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507023"
---
# <a name="permissive--standards-conformance"></a>/permissive- (標準一致性)

指定編譯器的標準一致性模式。 使用此選項可協助您找出並修正程式碼中的一致性問題，使其更正確且更具可攜性。

## <a name="syntax"></a>語法

> **`/permissive-`**

## <a name="remarks"></a>備註

Visual Studio 2017 和更新版本支援此選項。

您可以使用 **`/permissive-`** 編譯器選項來指定符合標準的編譯器行為。 這個選項會停用寬鬆的行為，並設定 [**`/Zc`**](zc-conformance.md) 嚴格符合性的編譯器選項。 在 IDE 中，此選項也會讓 IntelliSense 引擎為不符合規範的程式碼加上底線。

根據預設， **`/permissive-`** 選項會在 Visual Studio 2017 15.5 版和更新版本所建立的新專案中設定。 在舊版中，預設不會設定此版本。 設定選項時，編譯器會在您的程式碼中偵測到非標準語言結構時，產生診斷錯誤或警告。 這些結構包括 C + + 11 程式碼中的一些常見 bug。

此 **`/permissive-`** 選項可與最新 Windows 套件（例如軟體發展工具組（SDK）或 Windows 驅動程式套件（WDK））中幾乎所有的標頭檔相容，從 Windows 秋季建立者 SDK （10.0.16299.0）開始。 較舊版本的 SDK 可能會 **`/permissive-`** 因為各種原始程式碼一致性原因而無法編譯。 編譯器和 Sdk 隨附于不同的版本時間軸，因此有一些剩餘的問題。 如需特定的標頭檔問題，請參閱下面的[Windows 標頭問題](#windows-header-issues)。

**`/permissive-`** 選項會將 [**`/Zc:referenceBinding`**](zc-referencebinding-enforce-reference-binding-rules.md) 、 [**`/Zc:strictStrings`**](zc-strictstrings-disable-string-literal-type-conversion.md) 和選項設定 [**`/Zc:rvalueCast`**](zc-rvaluecast-enforce-type-conversion-rules.md) 為符合的行為。 這些選項預設為不符合規範的行為。 您可以在 **`/Zc`** 命令列之後傳遞特定選項 **`/permissive-`** ，以覆寫此行為。

從 Visual Studio 2017 版15.3 開始的編譯器版本中，選項會 **`/permissive-`** 設定 [**`/Zc:ternary`**](zc-ternary.md) 選項。 編譯器也會執行兩階段名稱查閱的更多需求。 **`/permissive-`** 設定選項時，編譯器會剖析函式和類別樣板定義，並識別範本中使用的相依和非相依名稱。 在此版本中，只會執行名稱相依性分析。

環境專屬的擴充功能和標準在執行上的語言區域不會受到的影響 **`/permissive-`** 。 例如，Microsoft 專有的 `__declspec` 呼叫慣例和結構化例外狀況處理關鍵字，以及編譯器專屬的 pragma 指示詞或屬性，在模式中不會標示為編譯器 **`/permissive-`** 。

**`/permissive-`** 選項會使用目前編譯器版本中的一致性支援來判斷哪些語言結構不符合規範。 選項不會判斷您的程式碼是否符合 c + + standard 的特定版本。 若要針對最新的草稿標準啟用所有已實現的編譯器支援，請使用 [**`/std:c++latest`**](std-specify-language-standard-version.md) 選項。 若要將編譯器支援限制為目前所實行的 c + + 17 標準，請使用 [**`/std:c++17`**](std-specify-language-standard-version.md) 選項。 若要限制編譯器支援，使其更符合 c + + 14 標準，請使用 [**`/std:c++14`**](std-specify-language-standard-version.md) 選項，這是預設值。

所有版本的 Visual Studio 2017 中的 MSVC 編譯器都不支援所有 c + + 11、c + + 14 或 c + + 17 標準一致的程式碼。 視 Visual Studio 版本而 **`/permissive-`** 定，選項可能無法偵測兩階段名稱查閱的某些層面中的問題、將非 const 參考系結至暫時的、將複製 init 視為直接 init、允許在初始化中使用多個使用者定義的轉換，或針對邏輯運算子使用替代的標記，以及其他不支援的一致性區域。 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 若要充分利用 **`/permissive-`** ，請將 Visual Studio 更新為最新版本。

### <a name="how-to-fix-your-code"></a>如何修正程式碼

以下是當您使用時，偵測為不符合規範的一些程式碼範例 **`/permissive-`** ，以及修正問題的建議方法。

#### <a name="use-default-as-an-identifier-in-native-code"></a>使用預設值做為機器碼中的識別碼

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>查詢相依基底中的成員

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>在成員宣告中使用限定名稱

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>初始化成員初始化運算式中的多個聯集成員

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
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>在陣列界限中使用範圍列舉

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>針對原生程式碼中的每個使用

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

#### <a name="use-of-atl-attributes"></a>ATL 屬性的使用

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

#### <a name="ambiguous-conditional-operator-arguments"></a>不明確的條件運算子引數

在 Visual Studio 2017 15.3 版之前的編譯器版本中，編譯器接受標準運算子（或三元運算子）的引數， `?:` 這會被視為不明確的。 在 **`/permissive-`** 模式中，編譯器現在會發出一或多個診斷，以在較早版本中未診斷的情況下進行編譯。

這種變更可能造成的常見錯誤包括：

- **`error C2593`**`: 'operator ?' is ambiguous`

- **`error C2679`**`: binary '?': no operator found which takes a right-hand operand of type 'B' (or there is no acceptable conversion)`

- **`error C2678`**`: binary '?': no operator found which takes a left-hand operand of type 'A' (or there is no acceptable conversion)`

- **`error C2446`**`: ':': no conversion from 'B' to 'A'`

當某些類別 C 同時提供來自另一個類型 T 的非明確函式，以及非明確的轉換運算子來輸入 T 時，可能會造成此問題的一般程式碼模式。在此情況下，第二個引數轉換成第三個引數的類型，而第三個引數轉換成第二個引數的類型是有效的轉換。 因為這兩者都是有效的，所以根據標準並不明確。

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

當 T 代表其中一個以 null 結束的字串類型（例如，、 `const char *` `const char16_t *` 等），且的實際引數 `?:` 是對應類型的字串常值時，這個常見的模式會有一個重要的例外狀況。 C + + 17 已變更 c + + 14 的語義。 因此，在中，會接受範例2中的程式碼， **`/std:c++14`** 並 **`/std:c++17`** 在 **`/Zc:ternary`** 使用或時拒絕 **`/permissive-`** 。

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

另一個您可能會看到錯誤的情況是在條件運算子中，其中有一個類型為的引數 **`void`** 。 這種情況在類似 ASSERT 的宏中可能很常見。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您也可能會在範本元使用者中看到錯誤，其中條件運算子結果類型可能會在和之下變更 **`/Zc:ternary`** **`/permissive-`** 。 解決此問題的其中一種方法是 [`std::remove_reference`](../../standard-library/remove-reference-class.md) 在產生的類型上使用。

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

設定此 **`/permissive-`** 選項時，編譯器會剖析函式和類別樣板定義，並根據兩階段名稱查閱的需求，識別範本中使用的相依和非相依名稱。 在 Visual Studio 2017 15.3 版中，會執行名稱相依性分析。 特別的是，未在範本定義內容中宣告的非相依名稱，會造成 ISO c + + 標準所需的診斷訊息。 在 Visual Studio 2017 15.7 版中，也會針對需要在定義內容中與引數相依的查詢進行系結的非相依名稱進行系結。

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

如果您想要讓兩階段查閱的舊版行為，但還是想要的 **`/permissive-`** 行為，請新增 **`/Zc:twoPhase-`** 選項。

### <a name="windows-header-issues"></a>Windows 標頭問題

在 **`/permissive-`** Windows 秋季建立者更新 SDK （10.0.16299.0）或 Windows 驅動程式套件（WDK）1709版之前，選項對 Windows 套件版本而言太嚴格。 建議您更新至 windows 套件的最新版本，以便 **`/permissive-`** 在 windows 或設備磁碟機程式碼中使用。

Windows 2018 年4月更新 SDK （10.0.17134.0）、Windows 秋季建立者更新 SDK （10.0.16299.0）或 Windows 驅動程式套件（WDK）1709中的特定標頭檔，仍然會有問題，使其與使用不相容 **`/permissive-`** 。 若要解決這些問題，我們建議您只將這些標頭的使用限制在需要它們的原始程式碼檔案，並 **`/permissive-`** 在編譯這些特定的原始程式碼檔案時移除選項。

Windows 2018 年4月更新 SDK （10.0.17134.0）中發行的這些 WinRT WRL 標頭並不會使用進行清除 **`/permissive-`** 。 若要解決這些問題，請不要使用 **`/permissive-`** ，或在 **`/permissive-`** **`/Zc:twoPhase-`** 您使用這些標頭時使用搭配：

- Winrt/wrl/async 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Winrt/wrl/implements 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Windows 2018 年4月更新 SDK （10.0.17134.0）中發行的這些使用者模式標頭並不會使用進行清除 **`/permissive-`** 。 若要解決這些問題，請 **`/permissive-`** 在使用這些標頭時不要使用：

- 在 um/微調 .h 中的問題

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Um/spddkhlp 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco 中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

這些問題專屬於 Windows 秋季建立者更新 SDK （10.0.16299.0）中的使用者模式標頭：

- 在 um/查詢 .h 中的問題

   使用 **`/permissive-`** 編譯器參數時， `tagRESTRICTION` 結構不會因為 Case （RTOr）成員 ' or ' 而編譯。

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

   若要解決此問題，請編譯包含 Query. h 但不含選項的檔案 **`/permissive-`** 。

- 在 um/cellularapi_oem 中的問題

   使用 **`/permissive-`** 編譯器參數時，的向前宣告 `enum UICCDATASTOREACCESSMODE` 會造成警告：

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   不限範圍列舉的向前宣告是 Microsoft 擴充功能。 若要解決此問題，請編譯包含 cellularapi_oem，但不含 **`/permissive-`** 選項的檔案，或使用 [**`/wd`**](compiler-option-warning-level.md) 選項來無聲警告 C4471。

- Um/omscript 中的問題

   在 c + + 03 中，從字串常值轉換成 BSTR （也就是 ' wchar_t * ' 的 typedef）已被取代，但允許使用。 在 c + + 11 中，已不再允許轉換。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   若要解決此問題，請編譯包含 omscript 但不含選項的檔案 **`/permissive-`** ，或改用 **`/Zc:strictStrings-`** 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

在 Visual Studio 2017 15.5 版和更新版本中，請使用此程式：

1. 開啟專案的 [**屬性頁**] 對話方塊。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **語言**] 屬性頁。

1. 將 [**一致性模式]** 屬性值變更為 **[是（/permissive-）]**。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

在 Visual Studio 2017 15.5 版之前的版本中，請使用此程式：

1. 開啟專案的 [**屬性頁**] 對話方塊。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中，輸入 **/permissive-** 編譯器選項。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
