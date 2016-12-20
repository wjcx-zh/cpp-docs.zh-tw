---
title: "Visual C++ 2015 Update 1 的重大變更 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Visual C++ 2015 Update 1 的重大變更
當您升級到 Visual C\+\+ 2015 Update 1 的新版本時，先前正常編譯及執行的程式碼可能會發生編譯和\/或執行階段錯誤。 編譯器或執行階段行為中會造成這類問題的變更稱為*「重大變更」*\(breaking change\)，在進行 C\+\+ 語言標準、函式簽章或記憶體內部物件配置的修改時通常都會有重大變更。  
  
 本文的其餘部分將描述 Visual C\+\+ 2015 Update 1 中的特定重大變更，在本文中，「新行為」或「現在」等詞彙指的就是這個版本。 「舊行為」和「之前」等詞彙指的是 Visual Studio 2015 和較早版本的初始版本。 如需 Visual Studio 2013 和 Visual Studio 2015 之間的重大變更相關資訊，請參閱 [Visual C\+\+ 2015 的重大變更](../porting/visual-cpp-change-history-2003-20151.md)。  
  
-   [編譯器的重大變更](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 編譯器  
  
-   **私用的虛擬基底類別和間接繼承**  
  
     舊版編譯器允許衍生的類別呼叫其*間接衍生*`private virtual` 基底類別的成員函式。 這個舊的行為不正確，而且不符合 C\+\+ 標準。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2280。  
  
 **錯誤 C2280：*'void \*S3::\_\_delDtor\(unsigned int\)'*：嘗試參考已刪除的函式**     範例 \(之前\)  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     \-或\-  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **多載的運算子 new 和運算子 delete**  
  
     舊版編譯器允許非成員 `operator new` 和非成員 `operator delete` 被宣告為靜態，以及在全域命名空間以外的命名空間中宣告。  這種舊行為造成的風險是，程式不會呼叫程式設計人員所預期的 `new` 或 `delete` 運算子實作，導致無訊息的錯誤執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2323。  
  
 **錯誤 C2323：*'operator new'*：非成員運算子 new 或 delete 函式可能不能被宣告為靜態，或不能在全域命名空間以外的命名空間中宣告。**     範例 \(之前\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     此外，雖然編譯器不提供特定的診斷，但內嵌運算子 new 會被視為語式錯誤。  
  
-   **在非類別類型上呼叫 'operator *type*\(\)' \(使用者定義轉換\)**  
  
     舊版編譯器允許在非類別類型上呼叫 'operator *type*\(\)'，但以無訊息方式略過。 這種舊行為造成的風險是，會產生無訊息的錯誤程式碼，導致無法預期的執行階段行為。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C2228。  
  
 **錯誤 C2228：'.operator *type*' 的左邊必須有類別\/結構\/等位**     範例 \(之前\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **複雜的類型規範中有重複的類型名稱**  
  
     舊版編譯器允許複雜的類型規範中有 `typename`，但這種方式撰寫的程式碼語意不正確。 編譯器不再接受以這種方式撰寫的程式碼，並會發出編譯器錯誤 C3406。  
  
 **錯誤 C3406：複雜的類型規範中不能使用 'typename'**     範例 \(之前\)  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **初始設定式清單的陣列類型推斷**  
  
     舊版編譯器不支援初始設定式清單的陣列類型推斷。 編譯器現在支援這種形式的類型推斷，而這樣一來，使用初始設定式清單呼叫函式範本現在可能會模稜兩可，也可能和舊版編譯器選擇不同的多載。 若要解決這些問題，程式現在必須明確指定程式設計人員所要的多載。  
  
     當這種新行為讓多載解析考慮和過去的候選項目同樣適合的其他候選項目時，呼叫就會變得模稜兩可，而編譯器則會發出編譯器錯誤 C2668。  
  
 **錯誤 C2668：'*function*'：模稜兩可地呼叫多載函式。**     範例 1：模稜兩可地呼叫多載函式 \(之前\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     範例 1：模稜兩可地呼叫多載函式 \(之後\)  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     當這種新行為讓多載解析考慮比過去的候選項目更適合的其他候選項目時，呼叫會明確解析為新的候選項目，讓程式行為變得和程式設計人員預期的不同。  
  
     範例 2：多載解析的變更 \(之前\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     範例 2：多載解析的變更 \(之後\)  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **還原 Switch 陳述式警告**  
  
     舊版編譯器移除了先前存在的和 `switch` 陳述式相關的警告，現在已還原這些警告。 編譯器現在會發出還原的警告，而與特定情況相關的警告 \(包括預設的情況\) 都會在包含違規情況的程式行發出，而不是在 switch 陳述式的最後一行發出。 現在，在和過去不一樣的程式行中發出警告的結果是，以前使用 `#pragma warning(disable:####)` 隱藏的警告，可能不會如預期隱藏起來。 若想要如預期隱藏這些警告，就必須將 `#pragma warning(disable:####)` 指示詞移至第一個可能違規情況的上一行。 以下是還原的警告。  
  
 **警告 C4060：switch 陳述式不包含 'case' 或 'default' 標籤 警告 C4061：case 標籤不會明確處理列舉 '*flags*' 參數中的列舉程式 '*bit1*' 警告 C4062：不處理列舉 '*flags*' 參數中的列舉程式 '*bit1*' 警告 C4063：案例 '*bit32*' 不是有效的列舉 '*flags*' 參數值 警告 C4064：不完整列舉 '*flags*' 的參數 警告 C4065：switch 陳述式包含 'default'，但沒有 'case' 標籤 警告 C4808：案例 '*value*' 不是有效的類型 '*bool*' 參數條件值 警告 C4809：switch 陳述式有重複的 'default' 標籤，已提供所有可能的 'case' 標籤**     C4063 範例 \(之前\)  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     C4063 範例 \(之後\)  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     其他還原警告的範例會於其各自文件中提供。  
  
-   **\#include：路徑名稱使用上層目錄指定名稱 '..'** \(只影響 \/Wall \/WX\)  
  
     舊版編譯器未偵測到 在 `#include` 指示詞的路徑名稱中是否使用上層目錄指定名稱 '..'。 以這種方式撰寫的程式碼通常會包含因為錯誤使用專案相對路徑而存在於專案以外的標頭。 這種舊行為造成的風險是，編譯程式時所包含的原始程式檔，可能不是程式設計人員想要的檔案，或是這些相對路徑無法移植到其他建置環境。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會發出選擇性的編譯器警告 C4464。  
  
 **警告 C4464：相對包含的路徑有 '..'**     範例 \(之前\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     此外，雖然編譯器不會提供特定的診斷，但我們還是建議應該使用上層目錄指定名稱 ".." 來指定專案的 include 目錄。  
  
-   **\#pragma optimize\(\) 擴充超出了標頭檔結尾** \(只會影響 \/Wall \/WX\)  
  
     舊版編譯器未偵測到最佳化旗標設定的變更，這會逸出包含在轉譯單位內的標頭檔。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在違反 `#include` 的位置發出選擇性的編譯器警告 C4426。 只有當變更與編譯器命令列引數設定的最佳化旗標發生衝突時，才會發出這個警告。  
  
 **警告 C4426：包含標頭之後最佳化旗標才變更，可能是因為 \#pragma optimize\(\)**     範例 \(之前\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **不相符的 \#pragma warning\(push\)** 和 **\#pragma warning\(pop\)** \(只會影響 \/Wall \/WX\)  
  
     舊版編譯器未偵測到 `#pragma warning(push)` 狀態變更和不同原始程式檔的 `#pragma warning(pop)` 狀態變更在配對，極少有人預期出現這種情況。這種舊行為造成的風險是，編譯程式所啟用的警告集合不是程式設計人員想要的集合，可能導致無訊息的錯誤執行階段行為。編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在符合 `#pragma warning(pop)` 的位置發出選擇性的編譯器警告 C5031。這個警告包含的附註，參考對應 \#pragma warning\(push\) 的位置。  
  
 **警告 C5031：\#pragma warning\(pop\)：可能不相符，彈出的警告狀態推入了不同的檔案**     範例 \(之前\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     雖不常見，但以這種方式撰寫的程式碼有時是故意為之。以這種方式撰寫的程式碼，對 `#include` 順序的變更相當敏感；如果可能的話，我們建議原始程式檔以獨立運作的方式管理警告狀態。  
  
-   **不相符的 \#pragma warning\(push\)** \(只會影響 \/Wall \/WX\)  
  
     舊版編譯器轉在轉譯單位的結尾未偵測到不相符的 `#pragma warning(push)` 狀態變更。 編譯器現在會偵測以這種方式撰寫的程式碼，並通知程式設計人員，如已啟用，還會在不符合 \#pragma warning\(push\) 的位置發出選擇性的編譯器警告 C5032。 只有轉譯單位沒有任何編譯錯誤時，才會發出這個警告。  
  
 **警告 C5032：偵測到沒有任何對應 \#pragma warning\(pop\) 的 \#pragma warning\(push\)**     範例 \(之前\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **因為追蹤改進的 \#pragma 警告狀態，可能會發出其他警告**  
  
     舊版編譯器過去追蹤 \#pragma 警告狀態變更的能力不佳，無法發出所有預期出現的警告。 這種行為造成的風險是，某些有效隱藏警告的情況，不是程式設計人員所預想的情況。 編譯器現在追蹤 \#pragma 警告狀態的能力更強大，特別是關於範本內部的 \#pragma 警告狀態變更，可以選擇性發出新的警告 C5031 和 C5032，它們的目的是協助程式設計人員找出非預期使用的 `#pragma warning(push)` 和 `#pragma warning(pop)`。  
  
     由於改良的 \#pragma 警告狀態變更追蹤，以前錯誤隱藏的警告或以前與錯誤診斷問題有關的警告，現在都可能會發出。  
  
-   **不可能執行到之程式碼的改進識別**  
  
     C\+\+ 標準程式庫的變更，以及比舊版編譯器強大的內嵌函式呼叫能力，可能會讓編譯器證明不可能執行到某些程式碼。 這種新行為可能會導致新的警告 C4720 的執行個體，且更頻繁地發出這個警告。  
  
 **警告 C4720：不可能執行到的程式碼**     在許多情況下，只有啟用最佳化編譯時，才可能發出這個警告；因為最佳化可能內嵌更多的函式呼叫、消除多餘的程式碼，或者可能判斷某不可能執行到些程式碼。 我們觀察到，新的警告 C4720 執行個體經常發生在 try\/catch 區塊，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) 時。  
  
     範例 \(之前\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```