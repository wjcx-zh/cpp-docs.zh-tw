---
title: /Zc:ternary (強制執行條件運算子規則)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335670"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (強制執行條件運算子規則)

啟用C++標準規則,用於條件運算符運算式中第二個和第三個操作數的類型和const 或易失性 (cv) 限定。

## <a name="syntax"></a>語法

> **/Zc:三元****-*** |

## <a name="remarks"></a>備註

從 Visual Studio 2017 開始,編譯器支援 C++標準*條件運算符***():**) 行為。 它也被稱為*三元運算子*。 C++標準要求三元操作數滿足三個條件之一:操作數必須相同類型和**條件**或**揮發性**限定(cv 限定),或者只有一個操作數必須明確轉換為與另一種類型和 cv 限定相同的操作數。 或者,一個或兩個操作數必須是引發表達式。 在 Visual Studio 2017 版本 15.5 之前的版本中,編譯器允許按標準認為不明確的轉換。

指定 **/Zc:三元**選項時,編譯器符合標準。 它拒絕不符合匹配類型規則的代碼以及第二個和第三個操作數的 cv 限定。

**/Zc:三元**選項在 Visual Studio 2017 中預設處於關閉狀態。 使用 **/Zc:三元**來啟用符合性行為,或 **/Zc:三元-** 顯式指定以前的不符合編譯器行為。 [/允許-](permissive-standards-conformance.md)選項隱式啟用此選項,但可以使用 **/Zc:ternary-** 重寫它。

### <a name="examples"></a>範例

此示例顯示提供類型非顯式初始化和轉換為類型的類如何導致不明確的轉換。 默認情況下,編譯器接受此代碼,但在指定 **/Zc:三元**或 **/允許時**拒絕。

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

要修復此代碼,請對首選公共類型進行顯式強制轉換,或防止類型轉換的一個方向。 通過顯式表示轉換,可以使編譯器與類型轉換匹配。

此常見模式的一個重要例外是,當操作數的類型是 null 終止字串類型之一,`const char*`如`const char16_t*`, 等。 您還可以使用數組類型及其衰減到的指標類型重現效果。 當實際的第二個或第三個操作數`?:`為相應類型的字串文本時的行為取決於所使用的語言標準。 C++17 已更改此案例的語義,從 C++14。 因此,編譯器在預設 **/std:c++14**下接受以下示例中的代碼,但在指定 **/std:c++17**時拒絕它。

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

要修復此代碼,請顯式轉換其中一個操作數。

在 **/Zc:ternary**下,編譯器拒絕條件運算符,其中一個參數的類型為**void,** 另一個不是引發表達式。 此模式的常見用在 ASSERT 類似巨集中:

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

典型的解決方案是用 替換非 void`void()`參數。

此範例顯示在 **/Zc:三元**與 **/Zc:三元 -** 下產生錯誤的代碼:

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

此代碼以前給出此錯誤:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

隨著 **/Zc:三元,** 失敗的原因變得更加清晰。 可以使用多個實現定義的調用約定中的任何一個生成每個 lambda。 但是,編譯器沒有首選項規則來消除可能的 lambda 簽名的歧義。 新輸出如下所示:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

**/Zc:ternary**發現的問題的常見來源來自範本元程式設計中使用的條件運算符。 某些結果類型在此開關下更改。 下面的範例演示了兩種情況,其中 **/Zc:ternary**在非元編程上下文中更改條件運算式的結果類型:

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

典型的解決方法是在結果類型上應用`std::remove_reference`特徵,在需要的地方保留舊行為。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇**配置屬性** > **C/C++** > **命令列**屬性頁。

1. 修改 **「附加選項」** 屬性以包括 **/Zc:三元**或 **/Zc:三元-** 然後選擇 **"確定**"。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
