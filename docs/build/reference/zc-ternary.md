---
title: '/Zc: ternary （強制執行條件運算子規則）'
ms.date: 3/06/2018
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: cb9a4f8468a9cb57af711cdca36ee343e5092493
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816486"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc: ternary （強制執行條件運算子規則）

啟用強制執行 c + + 標準類型的規則和條件運算子運算式中的第二個和第三個運算元的 const 或 volatile (cv) 限定性條件。

## <a name="syntax"></a>語法

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>備註

Visual Studio 15.3 版可讓編譯器支援 c + + 標準的條件式 （或三元） 運算子 (**？:**) 行為。 C + + 標準需要任一個運算元必須是相同的型別和 cv 限定只有一個運算元必須明確地轉換成相同的類型和 cv 限定為另一個，或是一個或兩個運算元都是 throw 運算式。 在 Visual Studio 15.5 版之前的版本中，編譯器會允許被視為由標準模稜兩可的轉換。 當 **/zc: ternary**指定選項時，編譯器符合標準，並拒絕不符合的規則相符的型別和 cv 限定的第二個和第三個運算元的程式碼。

**/Zc: ternary**選項預設為關閉。 使用 **/zc: ternary**若要啟用合格的行為，或是 **/Zc:ternary-** 來明確指定先前的不合格編譯器行為。 [/Permissive--](permissive-standards-conformance.md)選項會以隱含方式啟用此選項，但可以使用覆寫 **/Zc:ternary-**。

### <a name="examples"></a>範例

此範例會示範如何從一個型別和型別轉換提供這兩個非明確初始化的類別可能會導致模稜兩可的轉換。 根據預設，編譯器會接受這段程式碼，但遭到拒絕時 **/zc: ternary**或是 **/permissive--** 指定。

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

必要的修正是轉換的慣用的一般類型，請明確轉型，或藉由轉換明確防止一個方向型別比對編譯器搜尋的參與。

此一常見模式的重要例外狀況是當運算元的類型是一種 null 結束的字串類型，例如`const char*`， `const char16_t*`，依此類推。 您也可以重現這個陣列型別與它們 decay 以指標類型。 行為時要實際的第二個或第三個運算元？: 對應類型的字串常值取決於所使用的語言標準。 C++17 已變更語意，在此情況下的，從 C + + 14。 如此一來，在下列範例中的程式碼會接受底下 **/std: c + + 14** （編譯器預設值），但是遭到拒絕時 **/std: c + + 17**指定。

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

若要修正此程式碼，明確轉型的一個運算元。

底下 **/zc: ternary**、 編譯器拒絕條件式運算子其中一個引數為 void 類型和其他不是 throw 運算式。 這些的常見用法是在判斷提示式的巨集：

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

典型的解決方案是以 void() 取代非 void 引數。

這個範例會示範產生同時發生錯誤的程式碼 **/zc: ternary**並 **/Zc:ternary-**:

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

此程式碼中先前提供此錯誤：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

具有 **/zc: ternary**失敗的原因變得更清楚; 在其中的任何數個實作定義的呼叫慣例可用來產生每個 lambda 架構，編譯器會表示在它們之間沒有喜好設定可以釐清可能的 lambda 簽章。 新的輸出看起來像這樣：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

常見的問題來源與採用 **/zc: ternary**來自此交換器 下的部分結果型別變更範本中繼程式設計，在條件式運算子的用法。 下列範例示範兩種情況下所在 **/zc: ternary**變更非中繼程式設計內容中的條件運算式的結果類型：

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

一般的解決方式，在此情況下是套用`std::remove_reference`特性的結果類型，在需要時，若要保留舊的行為。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: ternary**或是 **/Zc:ternary-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
