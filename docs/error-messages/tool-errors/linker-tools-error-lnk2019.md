---
title: 連結器工具錯誤 LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 0ef0bfd565b8c76816cc1f8a20b1521da238cdfc
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447703"
---
# <a name="linker-tools-error-lnk2019"></a>連結器工具錯誤 LNK2019

無法解析的外部符號 '*符號*'中函式所參考的'*函式*'

已編譯的程式碼，如*函式*可讓參考或呼叫*符號*，但該符號未定義的任何程式庫或連結器指定的物件檔案。

此錯誤訊息後面接著嚴重錯誤[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 您必須修正所有 LNK2001 和 LNK2019 錯誤，若要修正錯誤 LNK1120。

## <a name="possible-causes"></a>可能的原因

有許多方法可取得這項錯誤，但所有人都牽涉到的函式或變數，連結器無法參考*解決*，或尋找的定義。 符號不是時，編譯器能夠識別*宣告*，但不是在未*定義*，因為定義可能是不同的原始程式檔或程式庫中。 如果符號為參考，但永遠不會定義，連結器會產生無法解析的外部符號錯誤。

以下是一些造成 LNK2019 的常見問題：

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>未連結的目的檔或程式庫包含的符號定義

在 Visual Studio 中，請確認包含定義的原始程式檔會建立並連結作為專案的一部分。 在命令列中，確認，就會包含定義的原始程式檔編譯，產生的物件檔案，會包含在要連結的檔案清單。

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>宣告與符號拼字與符號定義的相同

請確認正確的拼字和大小寫用於宣告和定義，而且符號為使用或呼叫的任一處。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>使用函式，但是類型或參數數目不相符的函式定義

函式宣告必須與定義相符。 請確認函式呼叫與宣告相符，而且宣告與定義相符。 叫用樣板函式的程式碼也必須有相符的樣板函式宣告，包含相同的樣板參數做為定義。 如需範本宣告不相符的範例，請參閱範例 LNK2019e.cpp 範例 > 一節中。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>函式或變數已宣告但未定義

這通常表示宣告存在於標頭檔，但並未實作任何相符的定義。 若為成員函式或靜態資料成員，實作必須包含類別範圍選取器。 如需範例，請參閱 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>呼叫慣例是在函式宣告和函式定義之間不同

呼叫慣例 ([__cdecl](../../cpp/cdecl.md)、 [__stdcall](../../cpp/stdcall.md)、 [__fastcall](../../cpp/fastcall.md)或 [__vectorcall](../../cpp/vectorcall.md)) 會編碼為裝飾名稱的一部分。 確認呼叫慣例相同。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>符號已定義在 C 檔案中，但未在中使用 extern"C"宣告C++檔案

編譯為 C 的檔案中所定義的符號之裝飾名稱，不同於 C++ 檔案中所宣告的符號，除非您使用 [extern"C"](../../cpp/using-extern-to-specify-linkage.md) 修飾詞。 請確認宣告與每個符號的編譯連結相符。 同樣地，如果您在 C++ 檔案中定義將由 C 程式使用的符號，請在定義中使用 `extern "C"` 。

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>符號已定義為靜態，並稍後外部檔案參考

不同於 C，C++ 中 [全域常數](../../error-messages/tool-errors/global-constants-in-cpp.md) 有 `static` 連結。 若要解決這項限制，您可以在標頭檔中包含 `const` 初始設定，並將該標頭包含在 .cpp 檔案中，或者您可以將變數設為非常數，並使用常數參考來存取。

### <a name="a-static-member-of-a-class-is-not-defined"></a>未定義類別的靜態成員

靜態類別成員必須具有唯一的定義，否則將違反單一定義規則。 無法以內嵌進行定義的靜態類別成員，必須使用其完整名稱在一個來源檔案中加以定義。 如果未完全定義，則連結器會產生 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>組建相依性只定義為方案中的專案相依性

在舊版的 Visual Studio 中，此層級的相依性已經足夠。 不過，從 Visual Studio 2010 開始，Visual Studio 需要[專案對專案參考](/visualstudio/ide/managing-references-in-a-project)。 如果您的專案沒有專案對專案間的參考，您就有可能會收到這個連結器錯誤。 加入專案對專案間的參考來修正此問題。

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>您使用之設定的 Windows 應用程式來建置主控台應用程式

如果錯誤訊息類似於**WinMain 函式中所參考的未解析外部符號** *function_name*，使用連結 **/subsystem: console**而不是 **/Subsystem: windows**。 如需此設定的詳細資訊，以及如何在 Visual Studio 中設定此屬性的指示，請參閱 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>您嘗試將 64 位元程式庫連結至 32 位元程式碼或 64 位元程式碼的 32 位元程式庫

必須針對與您的程式碼相同的架構編譯程式庫和物件檔案連結至您的程式碼。 確認您的專案參考針對與您的專案相同的架構編譯的程式庫。 請確定[/LIBPATH](../../build/reference/libpath-additional-libpath.md)或是**其他程式庫目錄**路徑指向正確的架構建置的程式庫的連結器所使用的選項。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>您的函式內嵌在不同的原始程式檔使用不同的編譯器選項

若使用在 .cpp 檔案中定義的內嵌函式，且又在不同的原始程式檔中混用函式內嵌編譯器選項，則可能會導致 LNK2019。 如需詳細資訊，請參閱 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>其範圍外部使用自動變數

自動 (函式範圍) 變數只能在該函式的範圍內使用。 不能將這些變數宣告為 `extern` ，也不能在其他原始程式檔中加以使用。 如需範例，請參閱 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>您呼叫內建函式，或傳遞至您的目標架構不支援的內建函式引數類型

例如，如果您使用 AVX2 內建，但未指定 [/ARCH:AVX2](../../build/reference/arch-x86.md) 編譯器選項，則編譯器會假設此內建為外部函式。 編譯器會產生具有相同名稱的外部符號呼叫做為內建，而非產生內嵌指令。 當連結器嘗試找出此遺漏函式的定義時，就會產生 LNK2019。 請確認您只使用內建和目標架構支援的型別。

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>您混合使用原生 wchar\_t 不的程式碼

C++已完成所做的 Visual Studio 2005 中的語言一致性工作`wchar_t`預設的原生型別。 您必須使用[/zc: wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)產生程式碼與使用舊版的 Visual Studio 所編譯的程式庫和目的檔相容的編譯器選項。 如果並非所有檔案都使用相同的已都編譯 **/Zc:wchar\_t**類型參考可能不會解析成相容的類型的設定。 在編譯時，請更新所使用的類型，或使用一致的 `wchar_t` 設定，以確認所有程式庫檔或目的檔中的 **/Zc:wchar_t** 類型都相容。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 Vcpkg

如果您嘗試將協力廠商程式庫設定為組建的一部分時，您會看到此錯誤，請考慮使用[Vcpkg](../../vcpkg.md)，視覺效果C++封裝管理員 中，安裝及建置程式庫。 Vcpkg 支援大量且不斷成長[協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並設定所有組態屬性和相依性所需的建置成功，為您專案的一部分。 如需詳細資訊，請參閱相關[VisualC++部落格](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="diagnosis-tools"></a>診斷工具

很難判斷為什麼連結器無法找到特定的符號定義。 問題通常是您不包含包含在您的組建定義的程式碼，或建置選項建立了不同裝飾外部符號的名稱。 有些工具和選項可協助您診斷 LNK2019 錯誤。

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 連結器選項可協助您判斷連結器會參考哪些檔案。 這可以協助您確認包含符號定義的檔案是否已包含在您的建置中。

- [/Exports](../../build/reference/dash-exports.md)並[/ 符號](../../build/reference/symbols.md)選項**DUMPBIN**公用程式可協助您探索哪些符號定義在.dll 和物件或程式庫檔案中。 請確認匯出的裝飾名稱與連結器搜尋的裝飾名稱相符。

- **UNDNAME**公用程式可以顯示裝飾名稱的對等未裝飾外部符號。

## <a name="examples"></a>範例

以下是幾個會造成 LNK2019 錯誤的範例程式碼，以及如何修正此錯誤的相關資訊。

### <a name="a-symbol-is-declared-but-not-defined"></a>符號已宣告但未定義

在此範例中，外部變數已宣告但未定義：

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

以下是另一個範例，其中宣告變數和函式為`extern`但不提供定義：

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

除非`i`和`g`定義在其中納入組建中的檔案中，連結器會產生 LNK2019。 您可以包含原始碼檔案來修正此問題，其中包含此定義做為編譯的一部分。 或者，您可以傳遞.obj 檔案或.lib 檔案，其中包含要連結器的定義。

### <a name="a-static-data-member-is-declared-but-not-defined"></a>靜態資料成員已宣告但未定義

LNK2019 也可能在靜態資料成員已宣告但未定義時發生。 下列範例會產生 LNK2019，並示範如何修正此問題。

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

### <a name="declaration-parameters-do-not-match-definition"></a>宣告參數與定義不相符

叫用樣板函式的程式碼必須具有對應的樣板函式宣告。 宣告必須包含相同的樣板參數做為定義。 下列範例會在使用者定義的運算子上產生 LNK2019，並示範如何修正此問題。

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
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

### <a name="inconsistent-wchart-type-definitions"></a>不一致的 wchar_t 類型定義

此範例會建立有一個使用 匯出的 DLL `WCHAR`，其解析後`wchar_t`。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

下一個範例會在前一個範例中，使用 DLL，並且會產生 LNK2019，因為類型不帶正負號短 * 和 WCHAR\*不相同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

若要修正這個錯誤，變更`unsigned short`要`wchar_t`或`WCHAR`，或藉由編譯 LNK2019g.cpp **/zc: wchar_t-**。

## <a name="additional-resources"></a>其他資源

如需 LNK2001 可能原因和解決方案的詳細資訊，請參閱 Stack Overflow 的問題[什麼是未定義參考/未解析的外部符號錯誤以及如何修正它？](http://stackoverflow.com/q/12573816/2002113)。

