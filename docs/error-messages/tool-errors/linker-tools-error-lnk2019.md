---
title: 連結器工具錯誤 LNK2019
description: 關於 Microsoft Visual Studio 連結器錯誤 LNK2019，以及如何在 C 和 c + + 程式碼中進行診斷和修正。
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- main
- WinMain
- wmain
- wWinMain
- __cdecl
- __stdcall
- __fastcall
- __vectorcall
- extern
- static
- const
- ARCH
- AVX2
- wchar_t
- VERBOSE
- EXPORTS
- SYMBOLS
- DUMPBIN
- UNDNAME
ms.openlocfilehash: d09e232b934761d138fee7324c462c915d919959
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509736"
---
# <a name="linker-tools-error-lnk2019"></a>連結器工具錯誤 LNK2019

> 函式 extern '*function*' 中參考了無法解析的 al 符號 '*symbol*'

針對函式編譯 *的程式* 代碼會進行參考或對 *符號*的呼叫，但連結器在程式庫或目的檔中找不到符號定義。

此錯誤訊息後面接著嚴重錯誤 [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 若要修正錯誤 LNK1120，您必須先修正所有的 LNK2001 和 LNK2019 錯誤。

## <a name="possible-causes"></a>可能的原因

有許多方法可以取得此錯誤。 它們都牽涉到連結器無法 *解析*的函式或變數參考，或是尋找的定義。 編譯器可以識別未宣告符號的時間 *，但*無法分辨符號未 *定義*的時間。 這是因為定義可能位於不同的原始程式檔或程式庫中。 如果有符號參考但從未定義，則連結器會產生無法解析的 extern al 符號錯誤。

以下是一些造成 LNK2019 的常見問題：

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>未編譯包含符號定義的原始程式檔

在 Visual Studio 中，請務必將定義符號的來源檔案編譯為專案的一部分。 檢查中繼組建輸出目錄中是否有相符的 .obj 檔案。 如果未編譯原始程式檔，請在方案總管中的檔案上按一下滑鼠右鍵，然後選擇 [ **屬性** ] 以檢查檔案的屬性。 [設定**屬性**  >  **一般**] 頁面應該會顯示**C/c + + 編譯器**的**專案類型**。 在命令列上，確定已編譯包含定義的原始程式檔。

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>未連結包含符號定義的物件檔案或程式庫

在 Visual Studio 中，請確定包含符號定義的物件檔案或程式庫已連結為專案的一部分。 在命令列上，確定要連結的檔案清單包含物件檔案或程式庫。

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>符號的宣告與符號的定義不會有相同的拼寫

請確認在宣告和定義中，以及使用或呼叫符號的任何位置，都使用正確的拼寫和大小寫。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>使用了函式，但參數的類型或數目與函式定義不相符

函式宣告必須與定義相符。 請確定函式呼叫符合宣告，且宣告符合定義。 叫用樣板函式的程式碼也必須有相符的樣板函式宣告，包含相同的樣板參數做為定義。 如需範本宣告不符的範例，請參閱範例一節中的範例 LNK2019e。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>已宣告函式或變數，但未定義

當宣告存在於標頭檔中，但未執行任何相符的定義時，就可能會發生 LNK2019。 若為成員函式或 static 資料成員，則實作為必須包含類別範圍選取器。 如需範例，請參閱 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>函式宣告和函式定義之間的呼叫慣例不同

呼叫慣例 ([__cdecl](../../cpp/cdecl.md) 、 [__stdcall](../../cpp/stdcall.md) 、 [__fastcall](../../cpp/fastcall.md) 或 [__vectorcall](../../cpp/vectorcall.md)) 會編碼為裝飾名稱的一部分。 請確定呼叫慣例相同。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>符號是在 C 檔案中定義，但在 extern c + + 檔案中未使用 "C" 宣告

編譯為 c 的檔案中所定義的符號具有不同的裝飾名稱，而非 c + + 檔案中所宣告的符號，除非您使用[ extern "C"](../../cpp/extern-cpp.md)修飾詞。 請確定宣告符合每個符號的編譯連結。 同樣地，如果您在 C++ 檔案中定義將由 C 程式使用的符號，請在定義中使用 `extern "C"` 。

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>符號定義為 static ，稍後在檔案外部參考

不同于 C，c + + 中的 [全域 const ants](../../error-messages/tool-errors/global-constants-in-cpp.md) 有 **`static`** 連結。 若要解決這項限制，您可以將 **`const`** 初始化包含在標頭檔中，並將該標頭包含在 .cpp 檔案中，或者您可以將變數設 const 為非 ant 並使用 const ant 參考來存取它。

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>static未定義類別的成員

static類別成員必須有唯一的定義，否則將會違反一個定義規則。 static無法以內嵌方式定義的類別成員，必須使用其完整名稱在一個原始程式檔中定義。 如果未定義，則連結器會產生 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>組建相依性只會定義為方案中的專案相依性

在舊版 Visual Studio 中，此層級的相依性就已足夠。 不過，從 Visual Studio 2010 開始，Visual Studio 需要 [專案對專案的參考](/visualstudio/ide/managing-references-in-a-project)。 如果您的專案沒有專案對專案的參考，您可能會收到此連結器錯誤。 加入專案對專案間的參考來修正此問題。

### <a name="an-entry-point-isnt-defined"></a>未定義進入點

應用程式程式碼必須定義適當的進入點： `main` 或 `wmain` 適用于主控台應用程式，以及 `WinMain` 或 `wWinMain` 適用于 Windows 應用程式。 如需詳細資訊，請參閱[ main 函數和命令列引數](../../cpp/main-function-command-line-args.md)或[ WinMain 函數](/windows/win32/api/winbase/nf-winbase-winmain)。 若要使用自訂進入點，請指定 [/ENTRY (進入點符號) ](../../build/reference/entry-entry-point-symbol.md) 連結器選項。

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>您使用 Windows 應用程式的設定來建立主控台應用程式

如果錯誤訊息類似于函式*function_name* ** extern WinMain 中參考的無法解析的 al 符號**，請使用 **/SUBSYSTEM： CONSOLE** （而不是 **/SUBSYSTEM： WINDOWS**）來連結。 如需此設定的詳細資訊，以及如何在 Visual Studio 中設定此屬性的指示，請參閱 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>您嘗試將64位程式庫連結至32位程式碼，或將32位程式庫連結至64位程式碼

連結至您程式碼的程式庫和物件檔案，必須針對與您的程式碼相同的架構進行編譯。 確定您專案所參考的程式庫會針對與您專案相同的架構進行編譯。 請確定 [ [/LIBPATH](../../build/reference/libpath-additional-libpath.md) ] 或 [ **其他程式庫目錄** ] 屬性指向針對正確架構所建立的程式庫。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>您可以在不同的原始程式檔中使用不同的編譯器選項來內嵌函數

若使用在 .cpp 檔案中定義的內嵌函式，且又在不同的原始程式檔中混用函式內嵌編譯器選項，則可能會導致 LNK2019。 如需詳細資訊，請參閱 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>您可以在其範圍外使用自動變數

自動 (函式範圍) 變數只能在該函式的範圍內使用。 這些變數無法 **`extern`** 在其他原始檔中宣告和使用。 如需範例，請參閱 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>您可以呼叫內建函式或將引數型別傳遞至目標架構上不支援的內建函式

例如，如果您使用內建 AVX2 ，但未指定[ / ARCH ： AVX2 ](../../build/reference/arch-x86.md)編譯器選項，則編譯器會假設內建函式為 al 函式 extern 。 編譯器不會產生內嵌指令，而是會使用與內建 extern 相同的名稱來產生 al.exe 符號的呼叫。 當連結器嘗試找出此遺漏函式的定義時，就會產生 LNK2019。 請確定您只使用目標架構所支援的內建函式和類型。

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>您將使用原生的程式碼混合 wchar_t 成不是

在 Visual Studio 2005 中完成的 c + + 語言一致性工作 **`wchar_t`** 預設為原生類型。 如果並非所有檔案都是使用相同的 **/zc： wchar_t ** settings 進行編譯，則類型參考可能無法解析成相容的類型。 請確定 **`wchar_t`** 所有文件庫和目的檔中的類型都相容。 **`wchar_t`** 當您編譯時，請從 typedef 進行更新，或使用一致的 **/zc： wchar_t **設定。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 vcpkg

如果您在嘗試將協力廠商程式庫設定為組建的一部分時看到此錯誤，請考慮使用 c + + 封裝管理員 [vcpkg](../../build/vcpkg.md)來安裝和建立程式庫。 vcpkg 支援大量且不斷成長 [的協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)。 它會將成功組建所需的所有設定屬性和相依性設定為專案的一部分。

## <a name="diagnosis-tools"></a>診斷工具

有時很難分辨為什麼連結器找不到特定的符號定義。 問題通常是您尚未在組建中包含包含定義的程式碼。 或者，組建選項已為 al 符號建立不同的裝飾名稱 extern 。 有數個工具和選項可協助您診斷 LNK2019 錯誤。

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)連結器選項可協助您判斷連結器所參考的檔案。 此選項可協助您確認您的組建中是否包含包含符號定義的檔案。

- [/EXPORTS](../../build/reference/dash-exports.md) [/SYMBOLS](../../build/reference/symbols.md) 公用程式的和選項 **DUMPBIN** 可協助您找出 .dll 和物件或程式庫檔案中定義的符號。 請確定匯出的裝飾名稱符合連結器搜尋的裝飾名稱。

- **UNDNAME** 公用程式可以向您顯示裝飾名稱的相等未修飾 extern al 符號。

## <a name="examples"></a>範例

以下是幾個會造成 LNK2019 錯誤的範例程式碼，以及如何修正此錯誤的相關資訊。

### <a name="a-symbol-is-declared-but-not-defined"></a>符號已宣告但未定義

在此範例中， extern 會宣告 al 變數，但未定義：

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

以下是另一個範例，其中變數和函式會宣告為， **`extern`** 但不提供定義：

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

除非 `i` 和 `g` 定義于組建中包含的其中一個檔案中，否則連結器會產生 LNK2019。 您可以包含原始碼檔案來修正此問題，其中包含此定義做為編譯的一部分。 或者，您可以將包含定義的 .obj 檔案或 .lib 檔案傳遞至連結器。

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>static資料成員已宣告但未定義

當 static 資料成員已宣告但未定義時，也會發生 LNK2019。 下列範例會產生 LNK2019，並示範如何修正此問題。

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-dont-match-the-definition"></a>宣告參數與定義不相符

叫用樣板函式的程式碼必須具有對應的樣板函式宣告。 宣告必須包含相同的樣板參數做為定義。 下列範例會在使用者定義的運算子上產生 LNK2019，並示範如何修正此問題。

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>不一致的 wchar_t 類型定義

這個範例會建立一個 DLL，這個 DLL 的匯出會使用 `WCHAR` 將解析為的 **`wchar_t`** 。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

下一個範例會使用先前範例中的 DLL，並產生 LNK2019，因為類型 `unsigned short*` 和 `WCHAR*` 不相同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

若要修正這個錯誤，請變更 **`unsigned short`** 為 **`wchar_t`** 或 `WCHAR` ，或使用 **/Zc： wchar_t - **來編譯 lnk2019g.cpp .cpp。

## <a name="additional-resources"></a>其他資源

如需有關 LNK2001 的可能原因和解決方案的詳細資訊，請參閱 Stack Overflow 問題 [什麼是未定義參考/未解析的 extern al 符號錯誤，以及如何修正此問題？](https://stackoverflow.com/q/12573816/2002113)。
