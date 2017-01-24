---
title: "/openmp (啟用 OpenMP 2.0 支援) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/openmp"
  - "VC.Project.VCCLCompilerTool.OpenMP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/openmp 編譯器選項 [C++]"
  - "-openmp 編譯器選項 [C++]"
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /openmp (啟用 OpenMP 2.0 支援)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會讓編譯器去處理 `#pragma` [omp](../../preprocessor/omp.md)。  
  
## 語法  
  
```  
/openmp  
```  
  
## 備註  
 `#pragma omp` 是用來指定 [Directives](../../parallel/openmp/reference/openmp-directives.md)和 [Clauses](../../parallel/openmp/reference/openmp-clauses.md)。  若未在編譯中指定 **\/openmp**，則編譯器會忽略 OpenMP 子句和指示詞。  即使未指定 **\/openmp**，[OpenMP 函式](../../parallel/openmp/reference/openmp-functions.md)呼叫也會由編譯器加以處理。  
  
 以 **\/openmp** 進行編譯並使用 [Libraries](../../parallel/openmp/reference/openmp-libraries.md)的應用程式只能在 Windows 2000 \(含\) 以後版本的作業系統上執行。  
  
 以 **\/openmp** 和 **\/clr** 編譯的應用程式只能在單一應用程式定義域處理序中執行，不支援多個應用程式定義域。  也就是，執行模組建構函式 \(.cctor\) 時，它會偵測處理序是以 **\/openmp** 進行編譯，以及應用程式是否正載入非預設執行階段中。  如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)、[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 和 [混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。  
  
 如果您嘗試將以 **\/openmp** 和 **\/clr** 編譯的應用程式載入非預設應用程式定義域中，<xref:System.TypeInitializationException> 例外狀況將擲出偵錯工具之外，而 OpenMPWithMultipleAppdomainsException 例外狀況將擲入偵錯工具之內。  
  
 這些例外狀況也可能會在下列情況中引發：  
  
-   如果您的應用程式是以 **\/clr** 而不是以 **\/openmp** 編譯，是載入非預設應用程式定義域中，但其中處理序包含以 **\/openmp** 編譯的應用程式。  
  
-   如果您將 **\/clr** 應用程式傳遞至公用程式，例如 regasm.exe \([Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)\)，它會將其目標組件載入非預設應用程式定義域。  
  
 Common Language Runtime 的程式碼存取安全性在 OpenMP 區域中沒有作用。  如果您在平行區域之外套用 CLR 程式碼存取安全性屬性，它在平行區域之內將不會有任何作用。  
  
 Microsoft 建議您，不要使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>，或任何 CLR 程式碼存取安全性屬性，撰寫允許部分信任呼叫端的 **\/openmp** 應用程式。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 \[**C\/C\+\+**\] 節點。  
  
4.  請選取 \[**語言**\] 屬性頁。  
  
5.  修改 \[**OpenMP 支援**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>。  
  
## 範例  
 下列範例會顯示啟動 Threadpool 的一些效果與啟動後再使用 Threadpool 的效果比較。  假設是 x64、單一程式碼、雙重處理器，Threadpool 大概要花 16 毫秒啟動。  但啟動之後，Threadpool 的消耗極小。  
  
 以 **\/openmp** 編譯時，test2 的第二個呼叫所花費時間絕對不會超過以 **\/openmp\-** 編譯時，因為沒有 Threadpool 啟動。  在百萬次反覆運算時，第二次呼叫 test2，**\/openmp** 版比 **\/openmp\-** 版更快速，在 25 次反覆運算時，**\/openmp\-** 和 **\/openmp** 版暫存器都低於系統時鐘細微性。  
  
 因此，如果您在應用程式中只有一個迴圈，而它執行的時間少於 15 毫秒 \(根據您電腦上的額外負荷調整\)，**\/openmp** 也許就不適當，但如果超過這個時間，倒不妨考慮使用 **\/openmp**。  
  
```  
// cpp_compiler_options_openmp.cpp  
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <windows.h>  
  
volatile DWORD dwStart;  
volatile int global = 0;  
  
double test2(int num_steps) {  
   int i;  
   global++;  
   double x, pi, sum = 0.0, step;  
  
   step = 1.0 / (double) num_steps;  
  
   #pragma omp parallel for reduction(+:sum) private(x)  
   for (i = 1; i <= num_steps; i++) {  
      x = (i - 0.5) * step;  
      sum = sum + 4.0 / (1.0 + x*x);  
   }  
  
   pi = step * sum;  
   return pi;  
}  
  
int main(int argc, char* argv[]) {  
   double   d;  
   int n = 1000000;  
  
   if (argc > 1)  
      n = atoi(argv[1]);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
}  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)