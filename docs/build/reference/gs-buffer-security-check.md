---
title: "/GS (緩衝區安全性檢查) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.BufferSecurityCheck"
  - "VC.Project.VCCLCompilerTool.BufferSecurityCheck"
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "緩衝區 [C++]，緩衝區滿溢"
  - "緩衝區滿溢，編譯器 /GS 參數"
  - "GS 編譯器選項 [C++]"
  - "/GS 編譯器選項 [C++]"
  - "安全性檢查編譯器選項 [C++]"
  - "-GS 編譯器選項 [C++]"
  - "緩衝區 [C++]，避免滿溢"
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
caps.latest.revision: 40
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GS (緩衝區安全性檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵測到覆寫函式之傳回位址、例外狀況處理常式位址，或是某些參數型別的一些緩衝區滿溢。  造成緩衝區滿溢是駭客利用程式碼不會強制緩衝區大小限制的一種技術。  
  
## 語法  
  
```  
/GS[-]  
```  
  
## 備註  
 **\/GS** 預設為開啟。  如果您希望應用程式沒有任何安全性漏洞，請使用 **\/GS\-**。  如需 **\/GS**相關詳細資訊，請參閱[編譯器詳細的安全性檢查。](http://go.microsoft.com/fwlink/?linkid=7260)。  如需抑制緩衝區滿溢偵測的詳細資訊，請參閱 [safebuffers](../../cpp/safebuffers.md)。  
  
## 安全性檢查  
 在編譯器辨識為可能發生緩衝區滿溢問題的函式，編譯器會在傳回位址前於堆疊上配置空間。  在函式進入點上，配置的空間會載入於模組載入時計算一次的「*安全性 Cookie*」\(Security Cookie\)。  在結束函式時，以及在 64 位元作業系統上的框架回溯期間，都會呼叫 Helper 函式以確定 Cookie 的值依然相同。  不同的值表示可能已發生堆疊的覆寫。  如果偵測到不同的值，就會終止處理序。  
  
## GS 緩衝區  
 緩衝區滿溢安全性檢查是在「*GS 緩衝區*」\(GS Buffer\) 上執行。  GS 緩衝區可以是以下之一：  
  
-   大於 4 個位元組的陣列，有兩個以上的項目，且其項目類型不是指標類型。  
  
-   其大小在 8 位元組以上，而且不包含指標的資料結構。  
  
-   使用 [\_alloca](../../c-runtime-library/reference/alloca.md) 函式配置的緩衝區。  
  
-   包含 GS 緩衝區的任何類別或結構。  
  
 例如，下列陳述式會宣告 GS 緩衝區。  
  
```  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
 不過，下列陳述式沒有宣告 GS 緩衝區。  前兩個宣告包含指標型別的項目。  第三個和第四個陳述式所宣告的陣列太小。  第五個陳述式所宣告的結構，其大小在 x86 平台上不超過 8 個位元組。  
  
```  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## 初始化安全性 Cookie  
 **\/GS** 編譯器選項需要在使用安全性 Cookie 的任何函式執行之前，先初始化安全性 Cookie。  一旦進入 EXE 或 DLL 之後，就必須初始化此安全性 Cookie。  如果您使用預設 CRT 進入點 \(mainCRTStartup、wmainCRTStartup、WinMainCRTStartup、wWinMainCRTStartup 或 \_DllMainCRTStartup\)，就會自動完成此項。  如果您使用替代的進入點，就必須藉由呼叫 [\_\_security\_init\_cookie](../../c-runtime-library/reference/security-init-cookie.md)，以手動方式初始化安全性 Cookie。  
  
## 什麼受保護  
 **\/GS** 編譯器選項會保護下列項目：  
  
-   函式呼叫的傳回位址。  
  
-   函式之例外狀況處理常式的位址。  
  
-   有弱點的函式參數。  
  
 在所有平台上，**\/GS** 都會嘗試偵測進入傳回位址的緩衝區滿溢。  在 x86 和 x64 之類的平台上，會更容易利用緩衝區滿溢，因為這類平台使用的呼叫慣例都將函式呼叫的傳回位址儲存在堆疊上。  
  
 在 x86 上，如果函式使用例外狀況處理常式，編譯器也會插入安全性 Cookie 來保護函式之例外處理常式的位址。  在框架回溯期間會檢查這個 Cookie。  
  
 **\/GS** 會保護傳遞至函式中的「*有弱點的參數*」\(Vulnerable Parameter\)。  有弱點的參數是指標、C\+\+ 參考，或者是含有指標或 GS 緩衝的 C 結構 \(C\+\+ POD 型別\)。  
  
 有弱點的參數會先配置，然後才配置 Cookie 和本機變數。  緩衝區滿溢可以覆寫這些參數，  而且使用這些參數之函式中的程式碼，可能會在函式傳回及執行安全性檢查之前造成攻擊。  為了將此危險性降到最低，編譯器會在函式初構期間製作有弱點之參數的複本，並將它們放在任何緩衝區的儲存區域下。  
  
 在下列情況中，編譯器都不會製作有弱點參數的複本：  
  
-   不包含 GS 緩衝區的函式。  
  
-   未啟用最佳化 \([\/O 選項](../../build/reference/o-options-optimize-code.md)\)。  
  
-   具有可變引數清單 \(...\) 的函式。  
  
-   以 [naked](../../cpp/naked-cpp.md) 標記的函式。  
  
-   在第一個陳述式中包含內嵌組譯程式碼的函式。  
  
-   對於參數，只會以在緩衝區滿溢的事件中較不可能遭利用的方式來使用。  
  
## 什麼不受保護  
 **\/GS** 編譯器選項不能防止所有的緩衝區滿溢安全性攻擊。  例如：如果您在物件中有一個緩衝區和一個 vtable，緩衝區滿溢就可能會損毀 vtable。  
  
 即使您使用 **\/GS**，也請永遠嘗試撰寫沒有緩衝區滿溢的安全程式碼。  
  
#### 若要在 Visual Studio 中設定這個編譯器選項  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的專案，然後按一下 \[**屬性**\]。  
  
     如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在 \[**屬性頁的**\] 對話方塊中，按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**程式碼產生**\] 屬性頁。  
  
4.  修改 \[**緩衝區安全性檢查**\] 屬性。  
  
#### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。  
  
## 範例  
 這個範例會滿溢緩衝區。  這會使應用程式在執行階段失敗。  
  
```  
// compile with: /c /W1  
#include <cstring>  
#include <stdlib.h>  
#pragma warning(disable : 4996)   // for strcpy use  
  
// Vulnerable function  
void vulnerable(const char *str) {  
   char buffer[10];  
   strcpy(buffer, str); // overrun buffer !!!  
  
   // use a secure CRT function to help prevent buffer overruns  
   // truncate string to fit a 10 byte buffer  
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);  
}  
  
int main() {  
   // declare buffer that is bigger than expected  
   char large_buffer[] = "This string is longer than 10 characters!!";  
   vulnerable(large_buffer);  
}  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)