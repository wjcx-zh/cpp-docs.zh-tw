---
title: "/RTC (執行階段錯誤檢查) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rtc"
  - "VC.Project.VCCLCompilerTool.SmallerTypeCheck"
  - "VC.Project.VCCLCompilerTool.UninitializedVariableCheck"
  - "VC.Project.VCCLCompilerTool.StackFrameCheck"
  - "VC.Project.VCCLCompilerTool.BasicRuntimeChecks"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RTC1 編譯器選項 [C++]"
  - "/RTCc 編譯器選項 [C++]"
  - "/RTCs 編譯器選項 [C++]"
  - "/RTCu 編譯器選項 [C++]"
  - "__MSVC_RUNTIME_CHECKS 巨集"
  - "RTC1 編譯器選項"
  - "-RTC1 編譯器選項 [C++]"
  - "RTCc 編譯器選項"
  - "-RTCc 編譯器選項 [C++]"
  - "RTCs 編譯器選項"
  - "-RTCs 編譯器選項 [C++]"
  - "RTCu 編譯器選項"
  - "-RTCu 編譯器選項 [C++]"
  - "執行階段檢查, /RTC 選項"
  - "執行階段錯誤, 錯誤檢查"
  - "執行階段錯誤, 執行階段檢查"
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /RTC (執行階段錯誤檢查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

結合 [runtime\_checks](../../preprocessor/runtime-checks.md) pragma，用來啟用及停用執行階段錯誤檢查功能。  
  
## 語法  
  
```  
/RTC1  
/RTCc  
/RTCs  
/RTCu  
```  
  
## Arguments  
 `1`  
 相當於 **\/RTC**`su`。  
  
 `c`  
 將值指派給較小資料型別，而造成資料損失時，就會發出報告。  例如，如果型別 `short 0x101` 的值指派給型別 `char` 的變數。  
  
 這個選項將會報告您意圖截斷的情況，例如，您要將 `int` 的前八個位元傳回做為 `char` 的情況。  因為如果由於指派而遺失任何資訊，**\/RTC**`c` 就會造成執行階段錯誤，您可以遮蓋所需資訊，避免因 **\/RTC**`c` 而導致執行階段錯誤。  例如：  
  
```  
#include <crtdbg.h>  
  
char get8bits(int value, int position) {  
   _ASSERT(position < 32);  
   return (char)(value >> position);  
   // Try the following line instead:  
   // return (char)((value >> position) & 0xff);  
}  
  
int main() {  
   get8bits(12341235,3);  
}  
```  
  
 `s`  
 啟用堆疊框架 \(Stack Frame\) 執行階段錯誤檢查，如下所示：  
  
-   區域變數初始化成為非零值，  這可以協助找出在偵錯模式中執行時不會出現的錯誤。  與發行組建相比，偵錯組建中的堆疊變數有很大的可能仍然是零，因為在發行組建 \(Build\) 中編譯器會將堆疊變數最佳化。  一旦程式使用了堆疊的某一區域之後，它永遠不會被編譯器重設為零。  因此，後續未初始化的堆疊變數碰巧也使用相同的堆疊區域時，就可能會傳回先前使用這個堆疊記憶體時遺留下來的值。  
  
-   本機變數 \(例如陣列\) 之滿溢和不足的偵測。  當因為結構內的編譯器填補而存取記憶體時，**\/RTC**`s` 將不會偵測滿溢。  填補是透過使用 [align](../../cpp/align-cpp.md)、[\/Zp \(結構成員對齊\)](../../build/reference/zp-struct-member-alignment.md) 或 [pack](../../preprocessor/pack.md) 而發生，或者是您排列結構項目的方式，導致需要編譯器加入填補。  
  
-   偵測堆疊指標損毀的堆疊指標驗證。  堆疊指標損毀可能由於呼叫慣例不符合造成。  例如，您使用函式指標呼叫 DLL 中匯出為 [\_\_stdcall](../../cpp/stdcall.md) 函式，但是您向這個函式宣告指標為 [\_\_cdecl](../../cpp/cdecl.md)。  
  
 `u`  
 當變數未經初始化就被使用時回報。  例如，會產生`C4701` 的指令可能也會在 **\/RTC**`u` 之下產生執行階段錯誤。  任何會產生[編譯器警告 \(層級 1 和層級 4\) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) 的指令也會在 **\/RTC**`u` 之下產生執行階段錯誤。  
  
 不過，請考量下列程式碼片斷：  
  
```  
int a, *b, c;  
if ( 1 )  
b = &a;  
c = a;  // No run-time error with /RTCu  
```  
  
 如果變數可能已經過初始化，就不會在執行階段由 **\/RTC**`u` 加以報告。  例如，當一個變數經由指標賦予別名之後，編譯器就不會再追蹤這個變數也不會報告它未經初始化的使用情況。  實際上，您可以藉由利用其位址來初始化某一變數。  & 運算子在這種情況下的作用就像是指派運算子。  
  
## 備註  
 執行階段錯誤檢查是讓您在執行程式碼時找出問題的一種方式；如需詳細資訊，請參閱 [如何：使用原生執行階段檢查](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md)。  
  
 如果您使用任何 **\/RTC** 編譯器選項在命令列編譯您的程式，那麼在您程式碼中的任何 Pragma [optimize](../../preprocessor/optimize.md) 指令都會失敗，而且不會出現訊息，  這是因為執行階段錯誤檢查在發行 \(已最佳化的\) 組建中無效。  
  
 您應該使用 **\/RTC** 進行開發組建。**\/RTC** 不應該用於零售組建。  **\/RTC** 無法配合編譯器最佳化使用 \([\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)\)。  用 **\/RTC** 建置的程式影像會比用 **\/Od** 建置的程式影像稍微大一點，也稍微慢一點 \(最多會比 **\/Od** 組建慢百分之五\)。  
  
 當您使用任何 **\/RTC** 選項或 [\/GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) 時，將會定義 \_\_MSVC\_RUNTIME\_CHECKS 前置處理器指示詞。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**程式碼產生**\] 屬性頁。  
  
4.  修改下列一項屬性或兩者都修改：\[**基礎執行階段檢查**\] 或 \[**較小型別檢查**\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> 屬性。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [RTC sample](http://msdn.microsoft.com/zh-tw/b3415b09-f6fd-43dc-8c02-9a910bc2574e)