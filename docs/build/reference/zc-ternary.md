---
title: "/Zc:ternary （強制執行條件式運算子規則） |Microsoft 文件"
ms.date: 1/12/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:ternary
dev_langs:
- C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2c4f4e17d3cf72284ec68cf10e75824722d5440
ms.sourcegitcommit: ef2a263e193410782c6dfe47d00764263439537c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary （強制執行條件式運算子規則）

啟用強制執行 c + + 標準類型的規則和第二個和第三個運算元的條件運算子的運算式中的 const 或 volatile (cv) 限定性條件。

## <a name="syntax"></a>語法

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>備註

Visual Studio 版本 15.3 可讓 c + + 標準的條件式 （或三元） 運算子的編譯器支援 (**？:**) 行為。 C + + 標準需要的任一個運算元是相同的型別和 cv 限定，或可以明確地轉換為相同的類型和 cv-限定性條件與其他，只有一個運算元或是一個或兩個運算元都是擲回運算式。 在 Visual Studio 版本 15.5 之前的版本，編譯器會允許轉換視為模稜兩可的標準。 當**/Zc:ternary**指定選項時，編譯器會符合標準，並拒絕不符合的規則相符的型別和 cv 限定的第二個和第三個運算元的程式碼。

**/Zc:ternary**選項預設為關閉。 使用**/Zc:ternary**啟用合格的行為，或**/Zc:ternary-**明確指定先前的不合格編譯器行為。 [/ 寬鬆-](permissive-standards-conformance.md)選項可讓**/Zc:ternary**。 

### <a name="examples"></a>範例

這個範例會示範如何從類型及類型轉換提供這兩個非明確初始化的類別可能會導致模稜兩可的轉換。 根據預設，編譯器會接受此程式碼，但拒絕時**/Zc:ternary**或**/ 寬鬆-**指定。

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

必要的修正，就是慣用的一般類型，請明確轉型，或藉由轉換明確防止參與編譯器搜尋的型別比對從轉換的一個方向。

常見的模式的重要例外是當運算元的類型是一種 null 結束的字串類型，例如`const char*`， `const char16_t*`，依此類推。 您也可以重現這與陣列類型及它們 decay 以指標類型。 行為時的實際第二個或第三個運算元？: 就會根據所使用的語言標準的對應類型的字串常值。 C + + 17 已經針對此案例的語意從 C + + 14。 如此一來，在下列範例程式碼會接受在**/std:c + + 14** （編譯器預設值），且不被拒絕時**/std:c + + 17**指定。

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

若要修正此程式碼，明確轉型的其中一個運算元。

在下**/Zc:ternary**、 編譯器拒絕條件式運算子其中一個引數為 void 類型，另一個則不擲回運算式。 這些的常見用法是類似的判斷提示巨集：

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

只要將非 void 引數取代 void() 為一般的解決方案。

此範例顯示程式碼會產生錯誤底下都**/Zc:ternary**和**/Zc:ternary-**:

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

此程式碼事先這個錯誤：

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

與**/Zc:ternary**失敗的原因變得更清楚，則為在其中幾個實作定義的呼叫任何的慣例可用來產生每個 lambda 架構編譯器表示它們之間沒有喜好設定可以區分可能的 lambda 簽章。 新的輸出看起來像這樣：

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

採用相關問題的常見來源**/Zc:ternary**來自此交換器 下的部分結果型別變更範本中繼程式設計中, 條件運算子的使用。 下列範例會示範兩種情況下其中**/Zc:ternary**變更非中繼程式設計內容中的條件式運算式的結果型別：

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

在此情況下的一般解決方法是套用`std::remove_reference`特性的結果類型在需要時，若要保留舊的行為。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/Zc:ternary**或**/Zc:ternary-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)  
