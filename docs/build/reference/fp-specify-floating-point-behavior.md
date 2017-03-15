---
title: "/fp (指定浮點數行為) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.floatingPointModel"
  - "VC.Project.VCCLWCECompilerTool.FloatingPointExceptions"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.floatingPointModel"
  - "VC.Project.VCCLCompilerTool.FloatingPointExceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/fp 編譯器選項 [C++]"
  - "-fp 編譯器選項 [C++]"
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /fp (指定浮點數行為)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在原始程式碼檔中指定浮點數行為。  
  
## 語法  
  
```  
/fp:[precise | except[-] | fast | strict ]  
```  
  
## 旗標  
 **precise**  
 預設值。  
  
 藉由停用可以變更浮點計算精確度的最佳化運算，改善浮點測試相等和不等的一致性 \(為了維持嚴格的 ANSI 一致性，必須保有特定精確度\)。根據預設，在 x86 架構程式碼中，編譯器會使用處理器的 80 位元暫存器來存放浮點計算的中繼結果，  這樣可以加快程式的速度並且縮小程式的大小。  不過，由於計算會涉及在記憶體中以小於 80 位元表示的浮點數資料類型，因此帶著額外的精確度位元 \(80 位元減去較小浮點類型中的位元數目\) 歷經冗長的計算，可能會產生不一致的結果。  
  
 有了 x86 處理器上的 **\/fp:precise**，編譯器就能在 `float` 類型的變數上執行捨入，以及在傳遞參數至函式時，取得指派和轉型的正確精確度。  這種捨入方式可保證該資料不保留任何大於其類型容量的數字精確度。  以 **\/fp:precise** 編譯的程式速度可能會比不是使用 **\/fp:precise** 編譯的程式更慢，而且體積更大。  **\/fp:precise** 會停用內建，而改用標準執行階段程式庫常式。  如需詳細資訊，請參閱 [\/Oi \(產生內建函式\)](../../build/reference/oi-generate-intrinsic-functions.md)。  
  
 下列浮點數行為是以 **\/fp:precise** 啟用：  
  
-   縮減：也就是使用結尾只有一次捨入的複合運算來取代多次運算。  
  
-   不允許對特殊值 \(NaN、\+infinity、\-infinity、\+0、\-0\) 無效的運算式最佳化。  x\-x \=\> 0、x\*0 \=\> 0、x\-0 \=\> x、x\+0 \=\> x 和 0\-x \=\> \-x 最佳化作業可能因為各種原因而無效 \(請參閱 IEEE 754 和 C99 標準\)。  
  
-   編譯器可正確處理涉及 NaN 的比較。  例如，如果 `x` 為 NaN，而且涉及 NaN 的已排序比較引發例外狀況，則 x \!\= x 會判斷值為 **true**。  
  
-   運算式評估會遵循 C99 FLT\_EVAL\_METHOD\=2，但有以下例外狀況：當您為 x86 處理器進行設計程式時，由於 FPU 設定為 53 位元精確度，因此這會視為長雙精確度。  
  
-   剛好乘以 1.0 的乘法結果會轉換成使用其他因數，  x\*y\*1.0 會轉換成 x\*y。  同樣地，x\*1.0\*y 會轉換成 x\*y。  
  
-   剛好除以 1.0 的除法結果會轉換成使用被除數。  x\*y\/1.0 會轉換成 x\*y。  同樣地，x\/1.0\*y 會轉換成 x\*y。  
  
 在 [fenv\_access](../../preprocessor/fenv-access.md) 為 ON 時使用 **\/fp:precise** 會停用最佳化作業，例如，浮點運算式的編譯階段評估。  例如，如果您使用 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 變更捨入模式，而編譯器執行浮點數計算，除非 `fenv_access` 為 ON，否則您指定的捨入模式不會作用。  
  
 **\/fp:precise** 會取代 **\/Op** 編譯器選項。  
  
 **fast**  
 藉由放寬最佳化浮點運算的規則，在大部分情況下建立最快速的程式碼。  這樣會讓編譯器犧牲準確度和正確性，以最佳化浮點程式碼的速度。  指定 **\/fp:fast** 時，編譯器可能無法在指派陳述式、類型轉換或函式呼叫時正確捨入，而且可能不會捨入中繼運算式。  編譯器可能會藉由像是遵循關聯和分散規則的方式重新排列運算或執行代數轉換，而不考慮對有限精確度結果的影響。  編譯器可能會將運算和運算元變更為單精確度，而不遵循 C\+\+ 類型提升規則。  浮點特定縮減最佳化一律為啟用狀態 \([fp\_contract](../../preprocessor/fp-contract.md) 為 ON\)。  浮點例外狀況和 FPU 環境存取為停用狀態 \(**\/fp:except\-** 為隱含且 [fenv\_access](../../preprocessor/fenv-access.md) 為 OFF\)。  
  
 **\/fp:fast** 無法與 **\/fp:strict** 或 **\/fp:precise** 搭配使用。  會使用命令列上指定的最後一個選項。  同時指定 **\/fp:fast** 和 **\/fp:except** 會產生編譯器錯誤。  
  
 指定 [\/Za、\/Ze \(停用語言擴充功能\)](../../build/reference/za-ze-disable-language-extensions.md) \(ANSI 相容性\) 和 **\/fp:fast** 可能會造成無法預期的行為。  例如，單精確度浮點運算可能不會捨入為單精確度。  
  
 **except\[\-\]**  
 可靠的浮點例外狀況模型。  觸發例外狀況之後會立即引發例外狀況。  根據預設，這個選項為關閉狀態。  附加減號至選項會明確將該選項停用。  
  
 **strict**  
 最嚴謹的浮點模型。  **\/fp:strict** 會讓 [fp\_contract](../../preprocessor/fp-contract.md) 變成 OFF 並且讓 [fenv\_access](../../preprocessor/fenv-access.md) 變成 ON。  **\/fp:except** 是隱含的，可透過明確指定 **\/fp:except\-** 的方式停用。  搭配 **\/fp:except\-** 使用時，**\/fp:strict** 會強制執行嚴格浮點語意，但不考慮例外事件。  
  
## 備註  
 相同編譯中可以指定多個 **\/fp** 選項。  
  
 若要由函式控制浮點數行為，請參閱 [float\_control](../../preprocessor/float-control.md) pragma。  這會覆寫 **\/fp** 編譯器設定。  建議的理想設計做法是儲存並還原本機浮點行為：  
  
```css  
#pragma float_control(precise, on, push)  
// Code that uses /fp:precise mode  
#pragma float_control(pop)  
```  
  
 大部分與 **\/fp:strict**、**\/fp:except** \(及其對應 pragma\) 和 `fp_contract` pragma 有關的浮點最佳化作業都與電腦相關。  **\/fp:strict** 和 **\/fp:except** 兩者與 **\/clr** 不相容。  
  
 **\/fp:precise** 應該可滿足應用程式的大部分浮點需求。  您可以使用 **\/fp:except** 和 **\/fp:strict**，但是可能會使效能稍微降低。  如果效能是最重要的，那麼請考慮是否要使用 **\/fp:fast**。  
  
 **\/fp:strict**、**\/fp:fast** 和 **\/fp:precise** 是精確度 \(正確性\) 模式，  但一次只能有一個模式生效。  如果同時指定了 **\/fp:strict** 和 **\/fp:precise**，則編譯器會使用最後處理的那一個。  **\/fp:strict** 和 **\/fp:fast** 都不能指定。  
  
 如需詳細資訊，請參閱 [Microsoft Visual C\+\+ 浮點最佳化](http://msdn.microsoft.com/library/aa289157.aspx)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 \[**C\/C\+\+**\] 節點。  
  
4.  選取 \[**程式碼產生**\] 屬性頁。  
  
5.  修改 \[**浮點模型**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [Microsoft Visual C\+\+ 浮點最佳化](http://msdn.microsoft.com/library/aa289157.aspx)