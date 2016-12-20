---
title: "連結器工具錯誤 LNK2019 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_check_commonlanguageruntime_version"
  - "LNK2019"
  - "nochkclr.obj"
ms.assetid: 4392be92-195c-4eb2-bd4d-49cfac3ca291
caps.latest.revision: 39
caps.handback.revision: 37
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式 'function' 中所參考的未解析外部符號 'symbol'  
  
 連結器找不到 "`function`" 函式中使用的 "`symbol`" 外部符號定義。 有許多可能會造成此錯誤的問題。 本主題將協助您找出原因並尋找問題的解答。  
  
 *外部符號*是宣告的名稱，讓您在原始程式碼中用來指稱定義於另一個目的檔或程式庫檔的事物，例如外部函式或全域變數。 當每個目的檔中的所有外部符號參考都連結到應用程式或 DLL 時，連結器會負責加以解析。 如果連結器在任何連結的檔案中找不到外部符號的相符定義，它就會產生 LNK2019。 如果有符號定義的原始碼或程式庫檔案未包含在建置中，就可能會發生此錯誤。 如果連結器搜尋的名稱與程式庫檔或目的檔中定義該連結器的符號名稱不相符時，也可能會發生此錯誤。  
  
 使用 C\+\+ 連結的程式碼會使用 [名稱裝飾](../../error-messages/tool-errors/name-decoration.md)，亦稱為 *名稱修飾*，以用來將符號類型與呼叫慣例以及符號名稱的額外資訊進行編碼。*裝飾名稱 \(decorated name\)* 是連結器搜尋的名稱，用來解析外部符號。 由於它會成為符號的裝飾名稱之一部分，如果符號參考的宣告類型和符號定義的宣告類型不相符，可能會造成 LNK2019 錯誤。 此錯誤訊息說明外部符號及其裝飾名稱，以協助您尋找錯誤的原因。  
  
 **常見問題**  
  
 以下是一些造成 LNK2019 的常見問題：  
  
-   **符號宣告與符號定義的拼字不同。**請確認已使用正確的拼字。  
  
-   **使用了函式，但是類型或參數數目與函式定義不相符。**函式宣告必須與定義相符。 叫用樣板函式的程式碼也必須有相符的樣板函式宣告，包含相同的樣板參數做為定義。 請確認函式呼叫與宣告相符，而且宣告與定義相符。  
  
-   **已宣告函式或變數，但未定義。**這通常表示宣告存在於標頭檔中，但並未實作任何定義。 若為成員函式或靜態資料成員，實作必須包含類別範圍選取器。 如需範例，請參閱 [遺漏函式主體或變數](../../error-messages/tool-errors/missing-function-body-or-variable.md)。  
  
-   **呼叫慣例在函式宣告和函式定義之間不同。**呼叫慣例 \([\_\_cdecl](../../cpp/cdecl.md)、[\_\_stdcall](../../cpp/stdcall.md)、[\_\_fastcall](../../cpp/fastcall.md) 或 [\_\_vectorcall](../../cpp/vectorcall.md)\) 會編碼為裝飾名稱的一部分。 確認呼叫慣例相同。  
  
-   **C 檔案中定義了一個符號，但未在 C\+\+ 檔案中使用 extern "C" 宣告。**編譯為 C 的檔案中所定義的符號之裝飾名稱，不同於 C\+\+ 檔案中所宣告的符號，除非您使用 [extern"C"](../../cpp/using-extern-to-specify-linkage.md) 修飾詞。 請確認宣告與每個符號的編譯連結相符。  
  
     同樣地，如果您在 C\+\+ 檔案中定義將由 C 程式使用的符號，請在定義中使用 `extern "C"`。  
  
-   **符號已定義為靜態，而且稍後由檔案外部參考。**不同於 C，C\+\+ 中[全域常數](../../error-messages/tool-errors/global-constants-in-cpp.md)有 `static` 連結。 若要解決這項限制，您可以在標頭檔中包含 `const` 初始設定，並將該標頭包含在 .cpp 檔案中，或者您可以將變數設為非常數，並使用常數參考來存取。  
  
-   **未定義類別的靜態成員。**靜態類別成員必須具有唯一的定義，否則將違反單一定義規則。 無法以內嵌進行定義的靜態類別成員，必須使用其完整名稱在一個來源檔案中加以定義。 如果未完全定義，則連結器會產生 LNK2019。  
  
-   **建置相依性只定義為方案中的專案相依性。**在舊版的 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]中，此層級的相依性已經足夠。 不過，從 Visual Studio 2010 開始，[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 需要 [專案對專案間的參考](../Topic/Managing%20references%20in%20a%20project.md)。 如果您的專案沒有專案對專案間的參考，您就有可能會收到這個連結器錯誤。 加入專案對專案間的參考來修正此問題。  
  
-   **您使用 Windows 應用程式設定來建置主控台應用程式**。 如果錯誤訊息類似於 **unresolved external symbol WinMain referenced in function**`function_name`，請使用 **\/SUBSYSTEM:CONSOLE** 來連結，而非 **\/SUBSYSTEM:WINDOWS**。 如需此設定的詳細資訊，以及如何在 Visual Studio 中設定此屬性的指示，請參閱[\/SUBSYSTEM \(指定子系統\)](../../build/reference/subsystem-specify-subsystem.md)。  
  
-   **您可以使用不同的編譯器選項，在不同的原始程式檔中用於函式內嵌。**若使用在 .cpp 檔案中定義的內嵌函式，且又在不同的原始程式檔中混用函式內嵌編譯器選項，則可能會導致 LNK2019。 如需詳細資訊，請參閱[函式內嵌問題](../../error-messages/tool-errors/function-inlining-problems.md)。  
  
-   **您可在其範圍外部使用自動變數。**自動 \(函式範圍\) 變數只能在該函式的範圍內使用。 不能將這些變數宣告為 `extern`，也不能在其他原始程式檔中加以使用。 如需範例，請參閱 [自動 \(函式範圍\) 變數](../../error-messages/tool-errors/automatic-function-scope-variables.md)。  
  
-   **您呼叫內建函式，或傳遞至內建函式的引數類型在您的目標架構上並不支援。**例如，如果您使用 AVX2 內建，但未指定 [\/ARCH:AVX2](../../build/reference/arch-x86.md) 編譯器選項，則編譯器會假設此內建為外部函式。 編譯器會產生具有相同名稱的外部符號呼叫做為內建，而非產生內嵌指令。 當連結器嘗試找出此遺漏函式的定義時，就會產生 LNK2019。 請確認您只使用內建和目標架構支援的型別。  
  
-   **您混合了使用和不使用原生 wchar\_t 的程式碼。**根據預設，於 Visual C\+\+ 2005 中完成的 C\+\+ 語言一致性工作讓 `wchar_t` 成為原生類型。 您必須使用 [\/Zc:wchar\_t\-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 編譯器選項，以產生與使用舊版 Visual C\+\+ 所編譯程式庫檔及目的檔相容的程式碼。 如果有些檔未使用相同的 **\/Zc:wchar\_t** 設定編譯，則類型參考可能不會解析成相容的類型。 在編譯時，請更新所使用的類型，或使用一致的 **\/Zc:wchar\_t** 設定，以確認所有程式庫檔或目的檔中的 `wchar_t` 類型都相容。  
  
 如需 LNK2019 可能原因和解決方案的詳細資訊，請參閱這篇 Stack Overflow 的問題[什麼是未定義參考\/未解析的外部符號錯誤，以及如何加以修正？](http://stackoverflow.com/q/12573816/2002113)。  
  
 **診斷工具**  
  
 很難判斷為什麼連結器無法找到特定的符號定義。 問題通常出在於，您在建置中並未包含此程式碼，或建置選項建立了外部符號的不同裝飾名稱。 有些工具和選項可協助您診斷 LNK2019 錯誤。  
  
-   [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md) 連結器選項可協助您判斷連結器會參考哪些檔案。 這可以協助您確認包含符號定義的檔案是否已包含在您的建置中。  
  
-   DUMPBIN 公用程式的 [\/EXPORTS](../../build/reference/dash-exports.md) 和 [\/SYMBOLS](../../build/reference/symbols.md) 選項可協助您探索哪些符號定義在 .DLL 和物件或程式庫檔案中。 請確認匯出的裝飾名稱與連結器搜尋的裝飾名稱相符。  
  
-   UNDNAME 公用程式可以顯示裝飾名稱之對等的未裝飾外部符號。  
  
 **範例**  
  
 以下是幾個會造成 LNK2019 錯誤的範例程式碼，以及如何修正此錯誤的相關資訊。  
  
 **符號已宣告但未定義**  
  
 下列範例會產生 LNK2019，因為外部的符號已宣告但未定義：  
  
```cpp  
// LNK2019.cpp // Compile by using: cl /EHsc LNK2019.cpp // LNK2019 expected extern char B[100];   // B is not available to the linker int main() { B[0] = ' ';   // LNK2019 }  
```  
  
 以下是另一個範例：  
  
```cpp  
// LNK2019c.cpp // Compile by using: cl /EHsc LNK2019c.cpp // LNK2019 expected extern int i; extern void g(); void f() { i++; g(); } int main() {}  
```  
  
 如果 `i` 和 `g` 未在建置中的檔案定義，連結器就會產生 LNK2019。 您可以包含原始碼檔案來修正此問題，其中包含此定義做為編譯的一部分。 或者，您可以傳遞給連結器包含定義的 .obj 檔案或 .lib 檔案。  
  
 **靜態資料成員已宣告但未定義**  
  
 LNK2019 也可能在靜態資料成員已宣告但未定義時發生。 下列範例會產生 LNK2019，並示範如何修正此問題。  
  
```cpp  
// LNK2019b.cpp // Compile by using: cl /EHsc LNK2019b.cpp // LNK2019 expected struct C { static int s; }; // Uncomment the following line to fix the error. // int C::s; int main() { C c; C::s = 1; }  
```  
  
 **宣告參數與定義不相符**  
  
 叫用樣板函式的程式碼必須具有對應的樣板函式宣告。 宣告必須包含相同的樣板參數做為定義。 下列範例會在使用者定義的運算子上產生 LNK2019，並示範如何修正此問題。  
  
```cpp  
// LNK2019e.cpp // compile by using: cl /EHsc LNK2019e.cpp // LNK2019 expected #include <iostream> using namespace std; template<class T> class Test { // The operator<< declaration does not match the definition below: friend ostream& operator<<(ostream&, Test&); // To fix, replace the line above with the following: // template<typename T> friend ostream& operator<<(ostream&, Test<T>&); }; template<typename T> ostream& operator<<(ostream& os, Test<T>& tt) { return os; } int main() { Test<int> t; cout << "Test: " << t << endl;   // LNK2019 unresolved external }  
```  
  
 **不一致的 wchar\_t 類型定義**  
  
 下列範例會建立 DLL，具有使用 `WCHAR` 的匯出，這會解析為 `wchar_t`。  
  
```cpp  
// LNK2019g.cpp // compile with: cl /EHsc /LD LNK2019g.cpp #include "windows.h" // WCHAR resolves to wchar_t __declspec(dllexport) void func(WCHAR*) {}  
```  
  
 下列範例會使用前一個範例中的 DLL，並且會產生 LNK2019，因為此類型之不帶正負號的 short\* 和 WCHAR \* 並不相同。  
  
```cpp  
// LNK2019h.cpp // compile by using: cl /EHsc LNK2019h LNK2019g.lib // LNK2019 expected __declspec(dllimport) void func(unsigned short*); int main() { func(0); }  
```  
  
 若要解決這個錯誤，請將 `unsigned short` 變更為 `wchar_t` 或 `WCHAR`，或使用 **\/Zc:wchar\_t\-** 編譯 LNK2019g.cpp。