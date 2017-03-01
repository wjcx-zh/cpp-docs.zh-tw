---
title: "連結器工具錯誤 LNK2019 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.assetid: 4392be92-195c-4eb2-bd4d-49cfac3ca291
caps.latest.revision: 39
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 86b43f2688b6e1dbfb39dfec681ca9adafd2c093
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2019"></a>連結器工具錯誤 LNK2019
函式 'function' 中所參考的未解析外部符號 'symbol'  
  
 連結器找不到 "`symbol`" 函式中使用的 "`function`" 外部符號定義。  
  
 有許多可能會造成此錯誤的問題。 本主題將協助您找出原因並尋找問題的解答。  
  
 A*符號*是編譯器會使用函式或全域變數的名稱。 *外部符號*是用來參考不同的來源或目的檔中定義的符號名稱。 連結器必須*解決*，或尋找每個函式或連結到應用程式或 DLL 時，每個已編譯的檔案所使用的全域變數的外部符號定義。 如果連結器在任何連結的檔案中找不到外部符號的相符定義，它就會產生 LNK2019。  
  
 如果有定義符號的物件或程式庫檔案未包含在組建中，可能會發生此錯誤。 如果連結器搜尋的符號名稱，在程式庫或物件檔案中定義的符號名稱不相符時，它也會發生。 如果呼叫程式碼中的名稱的拼字錯誤、 使用不同大小寫、 使用不同的呼叫慣例，或指定不同的參數，也可能會發生。  
  
 使用 c + + 連結的程式碼會使用[名稱裝飾](../../error-messages/tool-errors/name-decoration.md)，亦稱為*名稱改變*，用來編碼的變數或函式的類型和呼叫慣例的符號名稱的額外資訊。 *裝飾名稱 (decorated name)* 是連結器搜尋的名稱，用來解析外部符號。 型別資訊會成為符號的裝飾名稱的一部分，因為如果外部使用該符號的宣告與符號已定義的宣告不相符，就可能會造成 LNK2019。 為了協助您找出錯誤的原因，錯誤訊息說明這兩個 「 易記名稱，「 原始程式碼，以及未解析的外部符號的裝飾的名稱 （括號中） 中使用的名稱。 您不需要知道如何將轉譯的裝飾的名稱，以可比較它與其他裝飾名稱。  
  
 **常見的問題**  
  
 以下是一些造成 LNK2019 的常見問題：  
  
-   **未連結的目的檔或程式庫包含的符號定義。** 在 Visual Studio 中，確認原始程式檔，其中包含定義會建立並連結為您專案的一部分。 在命令列中，確認，已編譯原始程式檔，其中包含定義，且要連結的檔案清單中，會包含產生的物件檔案。  
  
-   **宣告與符號拼字符號的定義相同。** 確認正確的拼字和大小寫用於宣告和定義，而且無論在何處使用或呼叫符號。  
  
-   **使用函式，但是類型或參數數目不相符的函式定義。** 函式宣告必須與定義相符。 請確認函式呼叫與宣告相符，而且宣告與定義相符。 叫用樣板函式的程式碼也必須有相符的樣板函式宣告，包含相同的樣板參數做為定義。 樣板宣告不相符的範例，請參閱範例 LNK2019e.cpp 範例一節中。  
  
-   **函式或變數已宣告但未定義。** 這通常表示宣告出現在標頭檔中，但是沒有相符的定義實作。 若為成員函式或靜態資料成員，實作必須包含類別範圍選取器。 如需範例，請參閱[遺漏函式主體或變數](../../error-messages/tool-errors/missing-function-body-or-variable.md)。  
  
-   **呼叫慣例是函式宣告和函式定義之間不同。** 呼叫慣例 ([__cdecl](../../cpp/cdecl.md)， [__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)) 會編碼為裝飾名稱的一部分。 確認呼叫慣例相同。  
  
-   **符號定義在 C 檔案中，但未在 c + + 檔案中使用 extern"C"宣告。** 編譯為 C 的檔案中定義的符號會有不同於 c + + 檔案中宣告，除非您使用的符號的裝飾的名稱[extern"C"](../../cpp/using-extern-to-specify-linkage.md)修飾詞。 請確認宣告與每個符號的編譯連結相符。  
  
     同樣地，如果您在 C++ 檔案中定義將由 C 程式使用的符號，請在定義中使用 `extern "C"` 。  
  
-   **符號是定義為靜態，而且稍後外部檔案參考。** 不同於 C，c + + 中[全域常數](../../error-messages/tool-errors/global-constants-in-cpp.md)有`static`連結。 若要解決這項限制，您可以在標頭檔中包含 `const` 初始設定，並將該標頭包含在 .cpp 檔案中，或者您可以將變數設為非常數，並使用常數參考來存取。  
  
-   **未定義類別的靜態成員。** 靜態類別成員必須具有唯一的定義，否則將違反單一定義規則。 無法以內嵌進行定義的靜態類別成員，必須使用其完整名稱在一個來源檔案中加以定義。 如果未完全定義，則連結器會產生 LNK2019。  
  
-   **建置相依性只定義為方案中的專案相依性。** 在舊版的 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]中，此層級的相依性已經足夠。 不過，從 Visual Studio 2010 開始[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]需要[專案對專案參考](/visualstudio/ide/managing-references-in-a-project)。 如果您的專案沒有專案對專案間的參考，您就有可能會收到這個連結器錯誤。 加入專案對專案間的參考來修正此問題。  
  
-   **您使用 Windows 應用程式設定來建置主控台應用程式**。 如果錯誤訊息類似**WinMain 參考函式中的未解析外部符號**`function_name`，使用連結**/subsystem: console**而不是**/SUBSYSTEM:WINDOWS**。 如需有關此設定，以及如何在 Visual Studio 中設定這個屬性的指示，請參閱[/SUBSYSTEM （指定子系統）](../../build/reference/subsystem-specify-subsystem.md)。  
  
-   **您可以使用不同的編譯器選項不同的原始程式檔中的內嵌函數。** 若使用在 .cpp 檔案中定義的內嵌函式，且又在不同的原始程式檔中混用函式內嵌編譯器選項，則可能會導致 LNK2019。 如需詳細資訊，請參閱[函式內嵌問題](../../error-messages/tool-errors/function-inlining-problems.md)。  
  
-   **您可以使用自動變數其範圍之外。** 自動 (函式範圍) 變數只能在該函式的範圍內使用。 不能將這些變數宣告為 `extern` ，也不能在其他原始程式檔中加以使用。 如需範例，請參閱[自動 （函式範圍） 變數](../../error-messages/tool-errors/automatic-function-scope-variables.md)。  
  
-   **您呼叫內建函式或引數型別傳遞至您的目標架構不支援的內建函式。** 例如，如果您使用 AVX2 內建函式，但未指定[/arch: avx2](../../build/reference/arch-x86.md)編譯器選項，編譯器會假設此內建為外部函式。 編譯器會產生具有相同名稱的外部符號呼叫做為內建，而非產生內嵌指令。 當連結器嘗試找出此遺漏函式的定義時，就會產生 LNK2019。 請確認您只使用內建和目標架構支援的型別。  
  
-   **您混合程式碼，並不會使用原生 wchar_t 的程式碼。** 根據預設，於 Visual C++ 2005 中完成的 C++ 語言一致性工作讓 `wchar_t` 成為原生類型。 您必須使用[/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)編譯器選項，來產生程式碼與使用舊版的 Visual c + + 所編譯的程式庫和物件檔案。 如果有些檔未使用相同的 **/Zc:wchar_t** 設定編譯，則類型參考可能不會解析成相容的類型。 在編譯時，請更新所使用的類型，或使用一致的 `wchar_t` 設定，以確認所有程式庫檔或目的檔中的 **/Zc:wchar_t** 類型都相容。  
  
 如需 LNK2019 可能原因和解決方案的詳細資訊，請參閱這篇 Stack Overflow 的問題 [什麼是未定義參考/未解析的外部符號錯誤，以及如何加以修正？](http://stackoverflow.com/q/12573816/2002113)。  
  
 **診斷工具**  
  
 很難判斷為什麼連結器無法找到特定的符號定義。 問題通常出在於，您在建置中並未包含此程式碼，或建置選項建立了外部符號的不同裝飾名稱。 有些工具和選項可協助您診斷 LNK2019 錯誤。  
  
-   [/Verbose](../../build/reference/verbose-print-progress-messages.md)連結器選項可協助您判斷連結器會參考哪些檔案。 這可以協助您確認包含符號定義的檔案是否已包含在您的建置中。  
  
-   [/EXPORTS](../../build/reference/dash-exports.md)和[/ 符號](../../build/reference/symbols.md)DUMPBIN 公用程式的選項可協助您探索哪些符號定義在.dll 和物件或程式庫檔案。 請確認匯出的裝飾名稱與連結器搜尋的裝飾名稱相符。  
  
-   UNDNAME 公用程式可以顯示裝飾名稱之對等的未裝飾外部符號。  
  
 **範例**  
  
 以下是幾個會造成 LNK2019 錯誤的範例程式碼，以及如何修正此錯誤的相關資訊。  
  
 **符號已宣告但未定義**  
  
 下列範例會產生 LNK2019，因為外部的符號已宣告但未定義：  
  
```cpp  
// LNK2019.cpp  
// Compile by using: cl /EHsc LNK2019.cpp  
// LNK2019 expected  
extern char B[100];   // B is not available to the linker  
int main() {  
   B[0] = ' ';   // LNK2019  
}  
```  
  
 以下是另一個範例：  
  
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
  
 如果 `i` 和 `g` 未在建置中的檔案定義，連結器就會產生 LNK2019。 您可以包含原始碼檔案來修正此問題，其中包含此定義做為編譯的一部分。 或者，您可以傳遞給連結器包含定義的 .obj 檔案或 .lib 檔案。  
  
 **靜態資料成員已宣告但未定義**  
  
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
  
 **宣告參數與定義不相符**  
  
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
  
 **不一致的 wchar_t 類型定義**  
  
 下列範例會建立 DLL，具有使用 `WCHAR`的匯出，這會解析為 `wchar_t`。  
  
```cpp  
// LNK2019g.cpp  
// compile with: cl /EHsc /LD LNK2019g.cpp  
#include "windows.h"  
// WCHAR resolves to wchar_t  
__declspec(dllexport) void func(WCHAR*) {}  
```  
  
 下列範例會在上一個範例中，使用的 DLL，並會產生 LNK2019，因為類型不帶正負號短 * 和 WCHAR\*不相同。  
  
```cpp  
// LNK2019h.cpp  
// compile by using: cl /EHsc LNK2019h LNK2019g.lib  
// LNK2019 expected  
__declspec(dllimport) void func(unsigned short*);  
  
int main() {  
   func(0);  
}  
```  
  
 若要解決這個錯誤，變更`unsigned short`至`wchar_t`或`WCHAR`，或使用編譯 LNK2019g.cpp **/Zc:wchar_t-**。
