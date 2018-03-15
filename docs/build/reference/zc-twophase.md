---
title: "/Zc:twoPhase-（停用兩階段的名稱查閱） |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4582a5532d9fd410224ee4174ca3973bfe539656
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-（停用兩階段的名稱查閱）

當**/Zc:twoPhase-**指定選項時，編譯器會剖析並類別樣板和函式樣板會具現化相同的方式不合格 Visual Studio 2017 版本 15.3 之前的 Visual Studio 版本。 

## <a name="syntax"></a>語法

> **/Zc:twoPhase-**

## <a name="remarks"></a>備註

在 Visual Studio 2017 版本 15.3 及更新版本中，依預設，編譯器會使用兩階段的名稱查閱，進行範本的名稱解析。 如果**/Zc:twoPhase-**指定時，編譯器將回復到其先前不合格類別樣板和函式樣板名稱解析和替代的行為。

**/Zc:twoPhase-**選項來啟用不合格的行為不由預設設定。 [/ 寬鬆-](permissive-standards-conformance.md)選項會隱含地設定符合標準的兩階段查閱編譯器行為，但是可以使用覆寫**/Zc:twoPhase-**。

在 10.0.15063.0 （建立者更新或 Redstone 2） 的版本和舊版的 Windows SDK 標頭檔無法正常運作中的一致性模式。 您必須使用**/Zc:twoPhase-**來編譯程式碼的 SDK 版本，當您使用 Visual Studio 2017 版本 15.3 和更新版本。 版 10.0.15254.0 （Redstone 3 或年秋季建立者更新） 開頭的 Windows sdk 的版本一致性模式中運作正常，而且不需要**/Zc:twoPhase-**選項。

使用**/Zc:twoPhase-**如果您的程式碼需要舊的行為，才能正確編譯。 強烈建議考慮更新您的程式碼符合標準。

### <a name="compiler-behavior-under-zctwophase-"></a>/Zc:twoPhase-下的編譯器行為

在 Visual Studio 2017 版本 15.3 之前, 的編譯器版本及何時**/Zc:twoPhase-**指定，則編譯器會使用這種行為：

- 它會剖析樣板宣告、 類別標頭和基底類別清單。 語彙基元資料流的形式擷取的範本主體。 剖析的任何函式主體、 初始設定式、 預設引數或 noexcept 引數。 類別樣板是暫時性的型別，來驗證在類別樣板中的宣告的正確上具現虛擬化。 此類別範本，請考慮：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   樣板宣告， `template <typename T`>，類別標頭`class Derived`，和基底類別清單`public Base<T>`剖析，但是範本主體都擷取成語彙基元資料流。

- 當剖析函式樣板時，編譯器會剖析函式簽章。 永遠不會剖析函式主體。 相反地，它會被擷取成語彙基元資料流。

如此一來，如果範本主體有語法錯誤，而且永遠不會具現化樣板，永遠不會被診斷錯誤。

此行為的其他效果是多載解析。 因為在具現化的站台擴充語彙基元資料流的方式，而未顯示在樣板宣告的符號可能會出現在具現化，所以參與多載解析。 這可能會導致變更行為，所以看不到範本所定義時，fci 標準的程式碼為基礎的範本。

例如，請參考這個程式碼：

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main() 
{
    g(3.14);
}
```

在編譯時**/Zc:twoPhase-**，此程式會列印"的呼叫會解析為 int"。 在底下的一致性模式**/ 寬鬆-**，此程式會列印"呼叫會解析為 void *"，因為第二個多載的`func`看不到編譯器遇到範本時。

*相依名稱*，取決於樣板參數，必須也是在不同的查閱行為**/Zc:twoPhase-**。 在一致性模式中，相依名稱不會在範本的定義繫結。 相反地，這些名稱會查詢具現化範本時。 具有相依的函數名稱的函式呼叫，會顯示在範本的定義中，上述於呼叫的函式的集合是繫結的名稱。 從引數相依查閱其他多載會加入樣板定義的點和樣板具現化所在的點。 兩階段查閱的兩個階段的非相依名稱查閱時間在範本定義，而查閱相依名稱的樣板具現化時。 在下**/Zc:twoPhase-**，編譯器不會執行引數相依查閱分別從一般的不合格的查閱 （也就是它不會執行兩階段查閱），所以多載解析的結果可能會不同。

以下是另一個範例：

```cpp
// zctwophase1.cpp
// Compile by using
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

當將不會編譯**/Zc:twoPhase-**，列印

```Output
func(long)
NS::func(NS::S)
```

編譯時**/Zc:twoPhase-**，列印

```Output
func(int)
NS::func(NS::S)
```

一致性模式下**/ 寬鬆-**，呼叫`tfunc(1729)`解析成`void func(long)`未多載`void func(int)`多載下**/Zc:twoPhase-**，因為使用資格不符`func(int)`宣告樣板的定義之後，然後透過引數相依查閱找不到。 但是`void func(S)`因此它會新增至設定呼叫的多載，並未參與引數相依查閱`tfunc(s)`即使其宣告樣板函式之後。

### <a name="update-your-code-for-two-phase-conformance"></a>更新您的程式碼的兩階段交易的一致性

舊版編譯器不需要關鍵字`template`和`typename`everywhere c + + 標準需要它們。 這些關鍵字所需在某些位置，以釐清編譯器查閱的第一個階段期間剖析相依名稱的方式。 例如: 

`T::Foo<a || b>(c);`

合格編譯器剖析`Foo`的範圍中的變數`T`，這表示此程式碼是邏輯-或與運算式`T::foo < a`與左運算元和`b > (c)`為右運算元。 如果您想要使用`Foo`為函式範本，您必須指出這是範本，藉由新增`template`關鍵字：

`T::template Foo<a || b>(c);`

在 Visual Studio 2017 版本 15.3 之前, 的版本及何時**/Zc:twoPhase-**指定時，編譯器可讓此程式碼不含`template`關鍵字和解譯的引數與函式樣板呼叫`a || b`，因為它會剖析範本以非常有限的方式。 上述程式碼不是完全剖析第一個階段。 在第二個階段中，沒有足夠的內容，得知`T::Foo`是範本，而不是變數，所以編譯器不會強制使用關鍵字。

也可以藉由消除關鍵字看到這種行為`typename`之前的函式範本主體、 初始設定式、 預設引數和 noexcept 引數中的名稱。 例如: 

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果您不使用關鍵字`typename`函式主體中，這段程式碼會在編譯**/Zc:twoPhase-**，而不是會在**/ 寬鬆-**。 `typename`關鍵字，才能表示`TYPE`相依。 因為主體不會在剖析**/Zc:twoPhase-**，編譯器不需要的關鍵字。 在**/ 寬鬆-**一致性模式、 程式碼不含`typename`關鍵字會產生錯誤。 將您的程式碼移轉至 Visual Studio 2017 15.3 版本和更新版本，插入`typename`關鍵字已遺失。

同樣地，請考慮此程式碼範例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

在下**/Zc:twoPhase-** ，而在較舊的編譯器，編譯器只需要`template`第 2 行上的關鍵字。 根據預設，且符合模式中，編譯器現在也需要`template`關鍵字行 4 表示`T::X<T>`是範本。 尋找程式碼已遺失此關鍵字，並提供讓您符合標準的程式碼。

如需一致性問題的詳細資訊，請參閱[Visual Studio 中的 c + + 一致性改善](../../cpp-conformance-improvements-2017.md)和[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/Zc:twoPhase-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
