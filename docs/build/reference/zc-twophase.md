---
title: /Zc:twoPhase- (停用兩階段名稱查閱)
description: 說明在指定/permissive-時，/Zc： twoPhase-停用兩階段名稱查閱的方式。
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 712503d08221d29a61323946008f2f36a467cb31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234324"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (停用兩階段名稱查閱)

在 **/permissive-** 下， **/zc： twoPhase-** 選項會指示編譯器使用原始、不符合規範的 Microsoft c + + 編譯器行為來剖析和具現化類別樣板和函式樣板。

## <a name="syntax"></a>語法

> **/Zc： twoPhase-**

## <a name="remarks"></a>備註

Visual Studio 2017 15.3 版和更新版本：在[/permissive-](permissive-standards-conformance.md)底下，編譯器會針對範本名稱解析使用兩階段名稱查閱。 如果您也指定 **/zc： twoPhase-**，則編譯器會還原為先前不符合規範的類別範本，以及函式樣板名稱解析和替代行為。 未指定 **/permissive-** 時，不符合標準的行為是預設值。

版本10.0.15063.0 （建立者更新或 RS2）和較早版本中的 Windows SDK 標頭檔不會在一致性模式下執行。 **/Zc： twoPhase-** 當您使用 **/permissive-** 時，必須編譯這些 SDK 版本的程式碼。 從版本10.0.15254.0 （秋季建立者更新或 RS3）開始的 Windows SDK 版本會在一致性模式中正常運作。 它們不需要 **/zc： twoPhase-** 選項。

使用 **/zc： twoPhase-** 如果您的程式碼需要舊的行為才能正確編譯。 強烈考慮更新您的程式碼以符合標準。

### <a name="compiler-behavior-under-zctwophase-"></a>/Zc： twoPhase 下的編譯器行為

根據預設，或在 Visual Studio 2017 15.3 版和更新版本中，當您同時指定 **/permissive-** 和 **/zc： twoPhase-** 時，編譯器會使用此行為：

- 它只會剖析範本宣告、類別標頭和基類清單。 範本主體會以權杖資料流程的形式加以捕捉。 不會剖析任何函數主體、初始化運算式、預設引數或 noexcept 引數。 類別樣板在暫時類型上是虛擬具現化，用來驗證類別樣板中的宣告是否正確。 請考慮此類別範本：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   會剖析樣板宣告、 `template <typename T>` 、類別標頭 `class Derived` 和基類清單 `public Base<T>` ，但會將範本主體當做標記資料流程來加以捕捉。

- 剖析函式樣板時，編譯器只會分析函數簽章。 永遠不會剖析函式主體。 相反地，它會以權杖資料流程的形式加以捕捉。

因此，如果範本主體有語法錯誤，但範本永遠不會具現化，則編譯器不會診斷錯誤。

這個行為的另一個效果是多載解析。 發生非標準行為的原因，是因為在具現化的網站上展開標記資料流程的方式。 在具現化時，可能會顯示在範本宣告中看不到的符號。 這表示它們可以參與多載解析。 您可以根據在範本定義上看不到的程式碼，找到範本變更行為，這與標準相反。

例如，請思考下列程式碼：

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

當您搭配 **/zc： twoPhase-** 編譯器選項使用 [預設模式]、[一致性模式] 和 [一致性模式] 時，以下是輸出：

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

在 **/permissive-** 下以一致性模式編譯時，此程式會列印 " `Standard two-phase` "，因為 `func` 當編譯器到達範本時，的第二個多載不會顯示。 如果您新增 **/zc： twoPhase-**，程式會列印 " `Microsoft one-phase` "。 輸出與您未指定 **/permissive-** 時相同。

*相依名稱*是取決於範本參數的名稱。 這些名稱的查閱行為在 **/zc： twoPhase-** 之下也不同。 在一致性模式中，相依名稱不會在範本定義的位置系結。 相反地，編譯器會在具現化範本時尋找它們。 針對具有相依函式名稱的函式呼叫，會將名稱系結至範本定義中的呼叫位置所顯示的函式。 引數相依查閱的其他多載會在範本定義的位置，以及樣板具現化的點加入。

兩階段查閱包含兩個部分：在範本定義期間查閱非相依名稱，以及在範本具現化期間查閱相依名稱。 在 **/zc： twoPhase-** 底下，編譯器不會與不合格的查閱分開執行與引數相依的查閱。 也就是說，它不會執行兩階段查閱，因此多載解析的結果可能會不同。

以下是另一個範例︰

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

編譯而不 **/permissive-** 時，此程式碼會列印：

```Output
func(int)
NS::func(NS::S)
```

以 **/permissive-**（但不含 **/zc： twoPhase**）進行編譯時，此程式碼會列印：

```Output
func(long)
NS::func(NS::S)
```

以 **/permissive-** 和 **/zc： twoPhase**進行編譯時，此程式碼會列印：

```Output
func(int)
NS::func(NS::S)
```

在 **/permissive-** 下的一致性模式中，呼叫會 `tfunc(1729)` 解析為多載 `void func(long)` 。 它不會解析為多載 `void func(int)` ，如 **/Zc： twoPhase-**。 這是因為不合格的 `func(int)` 會在範本定義之後宣告，而且不會透過與引數相依的查閱找到。 但 `void func(S)` 會參與引數相依的查閱，因此它會加入至呼叫的多載集，即使它是在樣板函式之後宣告也 `tfunc(s)` 一樣。

### <a name="update-your-code-for-two-phase-conformance"></a>更新程式碼以符合兩個階段的一致性

較舊版本的編譯器不需要關鍵字 **`template`** 和 **`typename`** c + + 標準所需的任何位置。 某些位置需要這些關鍵字，以區別編譯器在查閱的第一個階段中，應如何剖析相依名稱。 例如：

`T::Foo<a || b>(c);`

符合規範的編譯器 `Foo` 會剖析為範圍中的變數 `T` ，這表示此程式碼是使用 `T::foo < a` 做為左運算元和右運算元的邏輯 or 運算式 `b > (c)` 。 如果您想要使用 `Foo` 做為函式範本，您必須藉由新增關鍵字來表示它是範本 **`template`** ：

`T::template Foo<a || b>(c);`

在版本 Visual Studio 2017 15.3 版和更新版本中，當指定 **/permissive-** 和 **/zc： twoPhase**時，編譯器會允許此程式碼不含 **`template`** 關鍵字。 它會將程式碼解釋為具有引數之函式樣板的呼叫 `a || b` ，因為它只會以有限的方式剖析範本。 在第一個階段中，不會剖析上述程式碼。 在第二個階段中，有足夠的內容可分辨 `T::Foo` 為範本，而不是變數，因此編譯器不會強制使用關鍵字。

在函式樣板 **`typename`** 主體、初始化運算式、預設引數和 noexcept 引數中的名稱前面排除關鍵字，也可以看到此行為。 例如：

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果您未在函 **`typename`** 式主體中使用關鍵字，此程式碼會在 **/permissive-/Zc： twoPhase-** 下編譯，但不會在 **/permissive-** 單獨進行。 **`typename`** 需要關鍵字來表示 `TYPE` 相依。 因為不會在 **/zc： twoPhase-** 下剖析本文，所以編譯器不需要關鍵字。 在 **/permissive-** 一致性模式中，沒有關鍵詞的程式碼會 **`typename`** 產生錯誤。 若要將您的程式碼遷移至 Visual Studio 2017 15.3 版和更高版本中的一致性，請插入 **`typename`** 遺漏的關鍵字。

同樣地，請考慮下列程式碼範例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

在 **/Permissive-/zc： twoPhase-** 和舊版編譯器中，編譯器只需要 **`template`** 第2行的關鍵字。 在一致性模式中，編譯器現在也需要 **`template`** 第4行上的關鍵字，以指出 `T::X<T>` 是範本。 尋找遺漏此關鍵字的程式碼，並提供它以讓您的程式碼符合標準。

如需一致性問題的詳細資訊，請參閱 Visual Studio 和[非標準行為](../../cpp/nonstandard-behavior.md)[中的 c + + 一致性改進](../../overview/cpp-conformance-improvements.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc： twoPhase** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
