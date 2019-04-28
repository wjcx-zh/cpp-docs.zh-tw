---
title: '/Zc: twophase-（停用兩階段名稱查閱）'
ms.date: 03/06/2018
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 5f990181fd1e606cf9d7dd33242752bed33aa456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315794"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc: twophase-（停用兩階段名稱查閱）

當 **/zc: twophase-** 指定選項時，編譯器會剖析並類別樣板和函式樣板會具現化相同的方式不合格 Visual Studio 2017 15.3 版之前的 Visual Studio 的版本。

## <a name="syntax"></a>語法

> **/Zc:twoPhase-**

## <a name="remarks"></a>備註

在 Visual Studio 2017 版本 15.3 和更新版本中，依預設，編譯器會使用兩階段名稱查閱的範本名稱解析。 如果 **/zc: twophase-** 指定，則編譯器會還原成其先前不合格類別樣板和函式範本名稱解析和替代的行為。

**/Zc: twophase-** 選項，以啟用不合格的行為不由預設設定。 [/Permissive--](permissive-standards-conformance.md)選項會隱含地設定符合的兩階段查閱編譯器行為，但可以使用覆寫 **/zc: twophase-**。

在 一致性模式，無法正常運作 （Creators Update 或 Redstone 2） 的 10.0.15063.0 版及之前版本的 Windows SDK 標頭檔。 您必須使用 **/zc: twophase-** 編譯的 SDK 版本的程式碼，當您使用 Visual Studio 2017 版本 15.3 和更新版本。 在 一致性模式中正確運作版 10.0.15254.0 （Redstone 3 或 Fall Creators Update） 開始的 Windows SDK 版本，而且不需要 **/zc: twophase-** 選項。

使用 **/zc: twophase-** 如果您的程式碼需要舊版行為，才能正確編譯。 慎重考慮更新您的程式碼，以符合標準。

### <a name="compiler-behavior-under-zctwophase-"></a>/Zc: twophase-下的編譯器行為

在 Visual Studio 2017 15.3 版中之前, 的編譯器版本及何時 **/zc: twophase-** 指定，則編譯器會使用這種行為：

- 它會剖析樣板宣告、 類別標頭和基底類別清單。 範本主體都擷取成語彙基元資料流。 會剖析任何函式主體，初始設定式、 預設引數或 noexcept 引數。 類別樣板是虛擬執行個體化，驗證中類別樣板的宣告正確的暫時性類型。 此類別範本，請考慮：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   樣板宣告中， `template <typename T`>，類別標頭`class Derived`，和基底類別清單`public Base<T>`剖析，但範本主體都會被擷取成語彙基元資料流。

- 剖析函式樣板時，編譯器會剖析函式簽章。 永遠不會剖析函式主體。 相反地，它會擷取為語彙基元資料流。

如此一來，如果範本主體有語法錯誤，而且永遠不會具現化的範本，會永遠不會診斷錯誤。

此行為的另一個的效果是多載解析。 因為在具現化的站台擴充語彙基元資料流的方式，未顯示在樣板宣告的符號可能會顯示在具現化時，參與多載解析。 這可能會導致變更行為沒有出現，範本已定義時，與標準的程式碼為基礎的範本。

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

下編譯時 **/zc: twophase-**，此程式會列印"呼叫解析為 int"。 在 一致性模式下 **/permissive--**，此程式會列印"呼叫解析成 void *，"因為第二個多載的`func`不可見，當編譯器遇到範本。

*相依名稱*，取決於樣板參數，必須也是在不同的查閱行為 **/zc: twophase-**。 在合規性模式中，相依名稱不會在範本的定義繫結。 相反地，這些名稱會尋找範本具現化時。 與相依的函數名稱的函式呼叫，會顯示在範本的定義，與上述中呼叫的函式集是繫結的名稱。 從引數相依查閱的其他多載會加入範本定義的點和樣板具現化所在的點。 兩階段查閱的兩個階段時之非相依名稱的查詢範本定義及對應的相依名稱的樣板具現化時。 底下 **/zc: twophase-**，編譯器不會執行引數相依查閱分別從一般的非限定的查閱 （也就是它不會執行兩階段查閱），所以多載解析的結果可能不同。

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

當編譯而不需要 **/zc: twophase-**，這會列印

```Output
func(long)
NS::func(NS::S)
```

編譯時 **/zc: twophase-**，這會列印

```Output
func(int)
NS::func(NS::S)
```

合規性模式下 **/permissive--**，呼叫`tfunc(1729)`解析`void func(long)`多載，不`void func(int)`多載下 **/zc: twophase-**，因為使用資格不符`func(int)`宣告範本的定義之後，然後透過引數相依查閱找不到。 但是`void func(S)`因此會新增至呼叫設定的多載，並未參與引數相依查閱，`tfunc(s)`即使其宣告的範本函式之後。

### <a name="update-your-code-for-two-phase-conformance"></a>更新您的程式碼的兩階段交易一致性

舊版編譯器不需要關鍵字`template`並`typename`everywhereC++標準需要它們。 這些關鍵字在某些位置才能釐清如何編譯器時，應該查閱的第一個階段期間剖析相依名稱。 例如: 

`T::Foo<a || b>(c);`

合格的編譯器剖析`Foo`的範圍中的變數`T`，這表示此程式碼是邏輯-或使用運算式`T::foo < a`為左運算元和`b > (c)`為右運算元。 如果您想要使用`Foo`做為函式範本中，您必須指出這是範本，藉由新增`template`關鍵字：

`T::template Foo<a || b>(c);`

在 Visual Studio 2017 15.3 版中之前, 的版本及何時 **/zc: twophase-** 指定時，編譯器可讓此程式碼，而不需要`template`關鍵字並將它解譯為使用引數函式樣板呼叫`a || b`，因為它會剖析範本，以非常有限的方式。 上述程式碼不是完全剖析中的第一個階段。 在第二個階段中，沒有足夠的內容，得知`T::Foo`是範本，而不是變數，所以編譯器不會強制使用關鍵字。

此行為也會顯示藉由消除關鍵字`typename`之前的函式範本主體、 初始設定式、 預設引數和 noexcept 引數中的名稱。 例如: 

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果您未使用關鍵字`typename`下，在函式主體中，編譯這個程式碼 **/zc: twophase-**，而不是會在 **/permissive--**。 `typename`關鍵字，才能指出`TYPE`相依。 因為主體都不會在剖析 **/zc: twophase-**，編譯器不需要關鍵字。 在  **/permissive--** 一致性模式，而不需要的程式碼`typename`關鍵字會產生錯誤。 若要將您的程式碼移轉至 Visual Studio 2017 15.3 版和以上版本之後，插入`typename`是缺少的關鍵字。

同樣地，請考慮此程式碼範例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

底下 **/zc: twophase-** ，而在舊版的編譯器中，編譯器只需要`template`第 2 行上的關鍵字。 根據預設，和合規性模式中，編譯器現在也需要`template`關鍵字的行 4 表示`T::X<T>`是範本。 尋找遺漏此關鍵字的程式碼，並提供它，讓您符合標準的程式碼。

如需一致性問題的詳細資訊，請參閱[ C++ Visual Studio 中的一致性改善](../../overview/cpp-conformance-improvements.md)並[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: twophase-** ，然後選擇**確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
