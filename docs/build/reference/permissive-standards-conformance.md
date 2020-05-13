---
title: /permissive- (標準一致性)
description: 微軟C++/允許(標準一致性)編譯器選項的參考指南。
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337408"
---
# <a name="permissive--standards-conformance"></a>/permissive- (標準一致性)

指定與編譯器的標準一致性模式。 使用此選項可説明您識別和修復代碼中的一致性問題,使其更加正確和可移植。

## <a name="syntax"></a>語法

> **/允許-**

## <a name="remarks"></a>備註

Visual Studio 2017 及更高版本支援此選項。

可以使用 **/允許編譯器**選項指定符合標準的編譯器行為。 此選項禁用允許行為,並設置[/Zc](zc-conformance.md)編譯器選項以嚴格一致性。 在 IDE 中,此選項還使 IntelliSense 引擎對不符合的代碼進行下劃線。

默認情況下 **,/允許選項**設置在 Visual Studio 2017 版本 15.5 和更高版本創建的新專案中。 默認情況下,它未在早期版本中設置。 設置該選項后,當在代碼中檢測到非標準語言構造(包括 C++11 代碼前的某些常見錯誤)時,編譯器將生成診斷錯誤或警告。

**/允許-** 選項與最新的 Windows 工具套件(如軟體開發工具組 (SDK) 或 Windows 驅動程式工具組 (WDK))中的幾乎所有標頭檔相容,這些配置檔從 Windows 秋季創建器 SDK (10.0.16299.0) 開始。 由於各種原始碼一致性的原因,舊版本的 SDK 可能無法在 **/允許下**編譯。 編譯器和 SDK 在不同的發佈時間線上提供,因此存在一些剩餘問題。 有關特定的標頭檔問題,請參閱下面的[Windows 標頭問題](#windows-header-issues)。

**/允許-** 選項將[/Zc:引用綁定](zc-referencebinding-enforce-reference-binding-rules.md)[、/Zc:嚴格字串](zc-strictstrings-disable-string-literal-type-conversion.md)和[/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md)選項設置為符合行為。 這些選項預設為不符合項行為。 您可以在命令列 **/允許**後傳遞特定的 **/Zc**選項以覆蓋此行為。

在 Visual Studio 2017 版本 15.3 中開始的編譯器版本中 **,/允許-** 選項設置[/Zc:三元](zc-ternary.md)選項。 編譯器還實現了兩階段名稱查找的更多要求。 設置 **/允許選項**時,編譯器將分析函數和類範本定義,並標識範本中使用的從屬和非從屬名稱。 在此版本中,僅執行名稱依賴項分析。

特定於環境的擴展和語言區域,標準留給實施不受 **/允許 -** 的影響。 例如,特定於 Microsoft`__declspec`的調用約定和結構化異常處理關鍵字以及編譯器特定的雜註指令或屬性不由編譯器在 **/允許模式下**標記。

**/允許-** 選項使用目前編譯器版本中的一致性支援來確定哪些語言構造不符合。 該選項不確定代碼是否符合C++標準的特定版本。 要啟用對最新標準草案的所有已實現編譯器支援,請使用[/std:最新](std-specify-language-standard-version.md)選項。 要將編譯器支援限制為當前實現的 C++17 標準,請使用[/std:c++17](std-specify-language-standard-version.md)選項。 要將編譯器支援限制為更緊密地匹配 C++14 標準,請使用[/std:c++14](std-specify-language-standard-version.md)選項,這是默認值。

並非所有 C++11、C++14 或 C++17 標準符合的代碼都受 Visual Studio 2017 所有版本中的 MSVC 編譯器的支援。 根據 Visual Studio 的版本 **,/允許-** 選項可能無法檢測有關兩階段名稱查找的某些方面的問題,將對臨時名稱查找的非引用綁定為直接 init,允許在初始化中允許多個使用者定義的轉換,或邏輯運算符的替代權杖以及其他不支援的符合性區域。 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。 要充分利用 **/允許-**,請將 Visual Studio 更新到最新版本。

### <a name="how-to-fix-your-code"></a>如何修復代碼

下面是一些在使用 **/允許時**檢測到不符合要求的代碼示例,以及修復問題的建議方法。

#### <a name="use-default-as-an-identifier-in-native-code"></a>使用預設值作為識別碼

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>尋找從屬基中的成員

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>在成員宣告中使用合格名稱

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>在成員初始化器中初始化多個工會成員

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

#### <a name="hidden-friend-name-lookup-rules"></a>隱藏好友名稱尋找規則

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

#### <a name="use-scoped-enums-in-array-bounds"></a>在陣列邊界中使用作用網域

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>在本機代碼中為每個使用

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

#### <a name="ambiguous-conditional-operator-arguments"></a>模糊的條件運算符參數

在 Visual Studio 2017 版本 15.3 之前編譯器的版本中,編譯器接受條件運算符(或三`?:`元運算符) 的參數,該參數被標準認為不明確。 在 **/允許模式下**,編譯器現在在在早期版本中編譯時沒有診斷的情況下發出一個或多個診斷。

此變更可能導致的常見錯誤包括:

- 錯誤 C2593:" "操作員?" 模棱兩可

- 錯誤 C2679: 二進位 '?': 找不到使用「B」類型右側操作數的運算符(或沒有可接受的轉換)

- 錯誤 C2678: 二進位 '?': 找不到類型為「A」的左側操作數的運算符(或沒有可接受的轉換)

- 錯誤 C2446:':':沒有從"B"轉換為"A"

可能導致此問題的典型代碼模式是,某些類 C 同時提供另一種類型的 T 的非顯式構造函數和類型 T 的非顯式轉換運算符。在這種情況下,將第二個參數轉換為第三個參數的類型以及將第三個參數轉換為第二個參數的類型都是有效的轉換。 由於兩者都有效,因此根據標準,它不明確。

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

當 T 表示 null 終止字串類型之一`const char *`(`const char16_t *`例如, 、`?:`、 等) 和實際 參數為相應類型的字串文本時,此常見模式有一個重要例外。 C++17 的語義從 C++14 進行了更改。 因此,在 **/std:c++14**下接受示例 2 中的代碼,並在**使用 /Zc:terna**或 **/允許時**在 **/std:c++17**下拒絕。

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

另一個可能看到錯誤的情況是條件運算符中,其中有一個`void`類型的參數。 這種情況在類似 ASSERT 的宏中可能很常見。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

您可能還會在範本元程式設計中看到錯誤,其中條件運算元結果類型可能在 **/Zc:terna**和 **/允許 -** 下更改。 解決此問題的一種方法是在生成的類型上使用[std::remove_reference。](../../standard-library/remove-reference-class.md)

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>兩階段名稱尋找

設置 **/允許選項**時,編譯器將分析函數和類範本定義,根據兩階段名稱查找所需的身份標識範本中使用的從屬名稱和非從屬名稱。 在 Visual Studio 2017 版本 15.3 中,將執行名稱依賴項分析。 特別是,未在範本定義上下文中聲明的非依賴名稱會導致 ISO C++標準所要求的診斷消息。 在 Visual Studio 2017 版本 15.7 中,還綁定了需要在定義上下文中尋找與參數相關的名稱。

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

如果希望對兩階段查找具有舊行為,但希望 **/允許行為**,則添加 **/Zc:雙相選項**。

### <a name="windows-header-issues"></a>Windows 標頭問題

**/允許-** 選項對於 Windows 秋季建立者更新 SDK (10.0.16299.0) 或 Windows 驅動程式工具組 (WDK) 版本 1709 之前的 Windows 工具套件版本太嚴格。 我們建議您更新到最新版本的 Windows 工具組,以便在 Windows 或設備驅動程式代碼中使用 **/允許。**

Windows 2018 年 4 月更新 SDK (10.0.17134.0)、Windows 秋季建立者更新 SDK (10.0.16299.0) 或 Windows 驅動程式工具組 (WDK) 1709 中的某些標題檔仍然存在問題,使它們與**使用 /允許 -** 不相容。 為了解決這些問題,我們建議您將這些標頭的使用限制為僅需要它們的原始程式碼檔案,並在編譯這些特定的原始程式碼檔時刪除 **/允許選項**。

在 Windows 2018 年 4 月更新 SDK (10.0.17134.0) 中發布的這些 WinRT WRL 標頭與 **/允許 -** 不幹凈。 要解決這些問題,請使用 **/允許 -** 或使用 **/Zc:兩階段** **-** 當您使用這些標頭時:

- winrt/wrl/非同步中的問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- 在 winrt/wrl/機具中發出問題。

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

在 Windows 2018 更新 SDK (10.0.17134.0) 中發布的這些使用者模式標頭與 **/允許 -** 不乾淨。 要解決這些問題,在使用這些標頭時,不要使用 **/允許**:

- 問題在 um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- 問題在嗯/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- 問題在嗯/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

這些問題特定於 Windows 秋季建立者更新 SDK (10.0.16299.0) 中的使用者模式標頭:

- 在 um/Query.h 中發生問題

   使用 **/允許 -** 編譯器開`tagRESTRICTION`關時, 結構不會編譯,因為 case(RTOr) 成員"或"。

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

   要解決此問題,請編譯包含 Query.h 的檔案,而不使用 **/允許選項**。

- 問題在嗯/cellularapi_oem.h

   使用 **/允許 -** 編譯器開關`enum UICCDATASTOREACCESSMODE`時,轉發 此錯誤會導致警告:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   未示影的枚舉的正向聲明是 Microsoft 擴展。 要解決此問題,請編譯包含 cellularapi_oem.h 的檔,而不使用 **/允許選項**,或使用[/wd](compiler-option-warning-level.md)選項來靜音警告 C4471。

- 問題在 um/omscript.h

   在 C++03 中,從字串文字轉換為 BSTR(即 typedef 轉換為"wchar_t +")被棄用,但允許。 在 C++11 中,不再允許轉換。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   要解決此問題,請編譯包含 omscript.h 的檔案,而不使用 **/允許選項**,或者使用 **/Zc:嚴格字串-**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

在 Visual Studio 2017 版本 15.5 和更高版本中,使用以下步驟:

1. 打開項目**的屬性頁**對話方塊。

1. 選擇**配置屬性** > **C/C++** > **語言**屬性頁。

1. 將 **「一致性模式**」 屬性值改變為 **「是」(/允許-)**。 選擇 **「確定」** 或 **「應用」** 以儲存變更。

在 Visual Studio 2017 版本 15.5 之前的版本中,使用以下步驟:

1. 打開項目**的屬性頁**對話方塊。

1. 選擇**配置屬性** > **C/C++** > **命令列**屬性頁。

1. 在 **'附加選項**'框中輸入 **/允許-** 編譯器選項。 選擇 **「確定」** 或 **「應用」** 以儲存變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
