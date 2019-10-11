---
title: 連結器工具錯誤 LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 3c4e5578c7b0f496feb4d40933af624f462a31d2
ms.sourcegitcommit: 680a155cc44a38f88bb2b1c5a1ef6dcb7141c011
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252632"
---
# <a name="linker-tools-error-lnk2019"></a>連結器工具錯誤 LNK2019

函式 '*function*' 中參考的未解析外部符號 '*symbol*'

針對函式編譯*的程式碼*會對*符號*進行參考或呼叫，但該符號不會定義在任何指定給連結器的程式庫或物件檔案中。

此錯誤訊息後面會接著嚴重錯誤[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 您必須修正所有 LNK2001 和 LNK2019 錯誤，以修正錯誤 LNK1120。

## <a name="possible-causes"></a>可能的原因

有許多方法可以取得此錯誤，但它們全都牽涉到連結器無法*解析*之函式或變數的參考，或尋找的定義。 編譯器可以*識別未宣告符號的時間*，而不是未*定義*時，因為定義可能位於不同的原始檔或程式庫中。 如果符號參考但從未定義過，則連結器會產生無法解析的外部符號錯誤。

以下是一些造成 LNK2019 的常見問題：

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>包含符號定義的物件檔案或程式庫並未連結

在 Visual Studio 中，確認包含定義的來源檔案已建立，並連結為專案的一部分。 在命令列上，確認包含定義的來源檔案已編譯，而且產生的物件檔案包含在要連結的檔案清單中。

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>符號的宣告與符號的定義不會有相同的拼寫

請確認宣告和定義中都使用正確的拼寫和大小寫，以及使用或呼叫符號的位置。

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>使用了函式，但參數的類型或數目不符合函式定義

函式宣告必須與定義相符。 請確認函式呼叫與宣告相符，而且宣告與定義相符。 叫用樣板函式的程式碼也必須有相符的樣板函式宣告，包含相同的樣板參數做為定義。 如需範本宣告不符的範例，請參閱範例 LNK2019e 一節中的範例。

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>已宣告函式或變數，但未定義

這通常表示存在於標頭檔中的宣告，但不會實作為相符的定義。 若為成員函式或靜態資料成員，實作必須包含類別範圍選取器。 如需範例，請參閱 [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md)。

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>呼叫慣例在函式宣告和函式定義之間不同

呼叫慣例 ([__cdecl](../../cpp/cdecl.md)、 [__stdcall](../../cpp/stdcall.md)、 [__fastcall](../../cpp/fastcall.md)或 [__vectorcall](../../cpp/vectorcall.md)) 會編碼為裝飾名稱的一部分。 確認呼叫慣例相同。

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>符號是在 C 檔案中定義，但不會在檔案中C++使用 Extern "C" 宣告

編譯為 C 的檔案中所定義的符號之裝飾名稱，不同於 C++ 檔案中所宣告的符號，除非您使用 [extern"C"](../../cpp/using-extern-to-specify-linkage.md) 修飾詞。 請確認宣告與每個符號的編譯連結相符。 同樣地，如果您在 C++ 檔案中定義將由 C 程式使用的符號，請在定義中使用 `extern "C"` 。

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>符號會定義為靜態，稍後在檔案外部參考

不同於 C，C++ 中 [全域常數](../../error-messages/tool-errors/global-constants-in-cpp.md) 有 `static` 連結。 若要解決這項限制，您可以在標頭檔中包含 `const` 初始設定，並將該標頭包含在 .cpp 檔案中，或者您可以將變數設為非常數，並使用常數參考來存取。

### <a name="a-static-member-of-a-class-is-not-defined"></a>未定義類別的靜態成員

靜態類別成員必須具有唯一的定義，否則將違反單一定義規則。 無法以內嵌進行定義的靜態類別成員，必須使用其完整名稱在一個來源檔案中加以定義。 如果未完全定義，則連結器會產生 LNK2019。

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>組建相依性只會定義為方案中的專案相依性

在舊版的 Visual Studio 中，此相依性層級已足夠。 不過，從 Visual Studio 2010 開始，Visual Studio 需要[專案對專案的參考](/visualstudio/ide/managing-references-in-a-project)。 如果您的專案沒有專案對專案間的參考，您就有可能會收到這個連結器錯誤。 加入專案對專案間的參考來修正此問題。

### <a name="an-entry-point-is-not-defined"></a>未定義進入點

應用程式代碼必須定義適當的進入點： `main` 或 `wmain` 代表主控台應用程式，`WinMain` 或 Windows 應用程式的 @no__t 3。 如需詳細資訊，請參閱 [main：程式啟動 @ no__t-0 或[WinMain 函數](/windows/win32/api/winbase/nf-winbase-winmain)。 若要使用自訂進入點，請指定[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)連結器選項。 

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>您可以使用 Windows 應用程式的設定來建立主控台應用程式

如果錯誤訊息類似于函式*function_name***中所參考的無法解析的外部符號 WinMain** ，請使用 **/SUBSYSTEM： CONSOLE** （而不是 **/SUBSYSTEM： WINDOWS**）進行連結。 如需此設定的詳細資訊，以及如何在 Visual Studio 中設定此屬性的指示，請參閱 [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md)。

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>您嘗試將64位程式庫連結至32位的程式碼，或將32位程式庫連結至64位程式碼

連結至您程式碼的程式庫和物件檔案，必須針對與您的程式碼相同的架構進行編譯。 確認您的專案所參考的程式庫會針對與您專案相同的架構進行編譯。 請確定連結器所使用的 [ [/LIBPATH](../../build/reference/libpath-additional-libpath.md) ] 或 [**其他程式庫目錄**] 路徑選項指向針對正確架構所建立的程式庫。

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>您在不同的原始程式檔中使用不同的編譯器選項來進行函式內嵌

若使用在 .cpp 檔案中定義的內嵌函式，且又在不同的原始程式檔中混用函式內嵌編譯器選項，則可能會導致 LNK2019。 如需詳細資訊，請參閱 [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md)。

### <a name="you-use-automatic-variables-outside-their-scope"></a>您在其範圍外使用自動變數

自動 (函式範圍) 變數只能在該函式的範圍內使用。 不能將這些變數宣告為 `extern` ，也不能在其他原始程式檔中加以使用。 如需範例，請參閱 [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md)。

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>您可以呼叫內部函式，或將引數類型傳遞至目標架構上不支援的內建函式

例如，如果您使用 AVX2 內建，但未指定 [/ARCH:AVX2](../../build/reference/arch-x86.md) 編譯器選項，則編譯器會假設此內建為外部函式。 編譯器會產生具有相同名稱的外部符號呼叫做為內建，而非產生內嵌指令。 當連結器嘗試找出此遺漏函式的定義時，就會產生 LNK2019。 請確認您只使用內建和目標架構支援的型別。

### <a name="you-mix-code-that-uses-native-wchar_t-with-code-that-doesnt"></a>您將使用原生 wchar @ no__t-0t 的程式碼混合成不是

C++根據預設，在 Visual Studio 2005 中進行的語言一致性工作 `wchar_t` 成為原生類型。 您必須使用[/zc： wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項，來產生與使用舊版 Visual Studio 所編譯之程式庫和物件檔案相容的程式碼。 如果未使用相同的 **/zc： wchar @ no__t-1t**設定來編譯所有檔案，則類型參考可能不會解析成相容的類型。 在編譯時，請更新所使用的類型，或使用一致的 `wchar_t` 設定，以確認所有程式庫檔或目的檔中的 **/Zc:wchar_t** 類型都相容。

## <a name="third-party-library-issues-and-vcpkg"></a>協力廠商程式庫問題和 Vcpkg

如果您在嘗試將協力廠商程式庫設定為組建的一部分時看到此錯誤，請考慮使用[Vcpkg](../../vcpkg.md)（Visual C++ Package Manager）來安裝和建立程式庫。 Vcpkg 支援大量且不斷成長[的協力廠商程式庫清單](https://github.com/Microsoft/vcpkg/tree/master/ports)，並將成功組建所需的所有設定屬性和相依性設為專案的一部分。 如需詳細資訊，請參閱相關的[視覺效果C++ Blog](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="diagnosis-tools"></a>診斷工具

很難判斷為什麼連結器無法找到特定的符號定義。 問題的原因通常是您尚未包含組建中包含定義的程式碼，或組建選項已針對外部符號建立不同的裝飾名稱。 有些工具和選項可協助您診斷 LNK2019 錯誤。

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 連結器選項可協助您判斷連結器會參考哪些檔案。 這可以協助您確認包含符號定義的檔案是否已包含在您的建置中。

- **DUMPBIN**公用程式的[/EXPORTS](../../build/reference/dash-exports.md)和[/SYMBOLS](../../build/reference/symbols.md)選項可協助您探索哪些符號定義在 .dll 和物件或程式庫檔案中。 請確認匯出的裝飾名稱與連結器搜尋的裝飾名稱相符。

- **Undname.exe**公用程式可以向您顯示裝飾名稱的對等未修飾外部符號。

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

以下是另一個範例，其中變數和函式宣告為 `extern`，但未提供任何定義：

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

除非在組建所包含的其中一個檔案中定義 `i` 和 `g`，否則連結器會產生 LNK2019。 您可以包含原始碼檔案來修正此問題，其中包含此定義做為編譯的一部分。 或者，您可以將包含定義的 .obj 檔案或 .lib 檔案傳遞至連結器。

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

### <a name="inconsistent-wchar_t-type-definitions"></a>不一致的 wchar_t 類型定義

這個範例會建立一個 DLL，其中具有使用 `WCHAR` 的匯出，它會解析成 `wchar_t`。

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

下一個範例會使用上一個範例中的 DLL，並產生 LNK2019，因為類型不帶正負號的 short * 和 WCHAR @ no__t-0 並不相同。

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

若要修正此錯誤，請將 `unsigned short` 變更為 `wchar_t` 或 `WCHAR`，或使用 **/zc： wchar_t-** 來編譯 lnk2019g.cpp。

## <a name="additional-resources"></a>其他資源

如需 LNK2001 可能原因和解決方案的詳細資訊，請參閱 Stack Overflow 問題[什麼是未定義參考/未解析的外部符號錯誤和如何修正？](https://stackoverflow.com/q/12573816/2002113)。

