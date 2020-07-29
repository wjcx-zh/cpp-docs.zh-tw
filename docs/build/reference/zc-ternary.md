---
title: /Zc:ternary (強制執行條件運算子規則)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 04bd0c49528d86ddd4d1e6c77804cf64278db188
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211875"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary`（強制執行條件運算子規則）

在條件運算子運算式中，針對第二個和第三個運算元的類型和 const 或 volatile （cv）限定性強制執行 c + + 標準規則。

## <a name="syntax"></a>語法

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>備註

從 Visual Studio 2017 開始，編譯器支援 c + + 標準*條件運算子*（ **`?:`** ）行為。 這也稱為*三元運算子*。 C + + 標準需要三元運算元滿足三個條件的其中一個：運算元必須是相同的類型和 **`const`** 或 **`volatile`** 限定性（cv 限定），或只有一個運算元必須明確轉換成與另一個相同的類型和 cv 限定性。 或者，其中一個或兩個運算元必須是 throw 運算式。 在 Visual Studio 2017 15.5 版之前的版本中，編譯器允許標準視為不明確的轉換。

當 **`/Zc:ternary`** 指定選項時，編譯器會符合標準。 它會拒絕不符合第二個和第三個運算元之符合類型和 cv 限定規則的程式碼。

**`/Zc:ternary`** 在 Visual Studio 2017 中，此選項預設為關閉。 使用 **`/Zc:ternary`** 來啟用符合的行為，或 **`/Zc:ternary-`** 明確指定先前不符合規範的編譯器行為。 [`/permissive-`](permissive-standards-conformance.md)選項會隱含啟用此選項，但是可以使用加以覆寫 **`/Zc:ternary-`** 。

### <a name="examples"></a>範例

這個範例會示範如何從類型提供非明確初始化以及轉換成類型的類別，可能會導致不明確的轉換。 根據預設，編譯器會接受此程式碼，但在 **/`Zc:ternary`** 指定或時拒絕 **`/permissive-`** 。

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

若要修正此程式碼，請明確轉換成慣用的一般類型，或避免轉換類型的一個方向。 您可以明確地進行轉換，讓編譯器不符合類型轉換。

這個常見模式的重要例外狀況是，當運算元的類型是其中一個以 null 終止的字串類型時，例如 `const char*` 、 `const char16_t*` 等等。 您也可以使用陣列類型及其衰減的指標類型來重現效果。 當實際的第二個或第三個運算元 `?:` 是對應類型的字串常值時，其行為取決於所使用的語言標準。 C + + 17 已變更 c + + 14 中此案例的語義。 因此，編譯器會在預設值下接受下列範例中的程式碼 **`/std:c++14`** ，但當您指定時，就會拒絕它 **`/std:c++17`** 。

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

若要修正此程式碼，請明確地轉換其中一個運算元。

在之下 **`/Zc:ternary`** ，編譯器會拒絕其中一個引數屬於類型 **`void`** ，而另一個不是運算式的條件運算子 **`throw`** 。 此模式的常見用法是在類似 ASSERT 的宏中：

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

一般的解決方法是將非 void 引數取代為 `void()` 。

這個範例會顯示在和下產生錯誤的程式碼 **`/Zc:ternary`** **`/Zc:ternary-`** ：

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

此程式碼先前已提供此錯誤：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

使用 **`/Zc:ternary`** 時，失敗的原因會變得更清楚。 任何一種實作為定義的呼叫慣例，都可以用來產生每個 lambda。 不過，編譯器沒有任何喜好設定規則來區分可能的 lambda 簽章。 新的輸出看起來像這樣：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

發現的常見問題來源來自于 **`/Zc:ternary`** 範本中繼程式設計中所使用的條件運算子。 某些結果類型會在此參數下變更。 下列範例示範 **`/Zc:ternary`** 在非中繼程式設計內容中變更條件運算式結果型別的兩個案例：

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

一般的修正方式是在 `std::remove_reference` 結果類型上套用特性，需要保留舊的行為。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **`/Zc:ternary`** 或 **`/Zc:ternary-`** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[`/Zc`標準](zc-conformance.md)
