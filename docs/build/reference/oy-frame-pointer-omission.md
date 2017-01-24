---
title: "/Oy (框架指標省略) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.OmitFramePointers"
  - "/oy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oy 編譯器選項 [C++]"
  - "框架指標省略編譯器選項 [C++]"
  - "省略框架指標"
  - "Oy 編譯器選項 [C++]"
  - "-Oy 編譯器選項 [C++]"
  - "堆疊框架指標編譯器選項 [C++]"
  - "隱藏框架指標的建立"
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Oy (框架指標省略)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在呼叫堆疊上隱藏框架指標的建立。  
  
## 語法  
  
```  
/Oy[-]  
```  
  
## 備註  
 這個選項會加速函式呼叫，因為並不需要設定及移除框架指標。  而且也能夠釋出更多暫存器 \(Intel 386 或以上的 EBP\)，以供儲存經常使用的變數和子運算式。  
  
 **\/Oy** 會啟用框架指標省略，而 **\/Oy\-** 會停用省略。 **\/Oy** 只可在 x86 編譯器中使用。  
  
 如果程式碼需要 EBP 架構定址，您可以在 **\/Ox** 選項之後指定 **\/Oy–** 選項，或使用 [optimize](../../preprocessor/optimize.md) 搭配 "**y**" 和 **off** 引數，以獲得對 EBP 架構定址的最大程度最佳化。  編譯器會偵測大部分需要 EBP 架構定址的情況 \(例如，對於 `_alloca` 和 `setjmp` 函式以及處理結構化例外狀況\)。  
  
 [\/Ox \(完全最佳化\)](../../build/reference/ox-full-optimization.md) 和 [\/O1、\/O2 \(最小大小、最快速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 選項隱含 **\/Oy**。  在 **\/Ox**、**\/O1** 或 **\/O2** 選項停用 **\/Oy** 以後，不論是明確或隱含，都指定 **\/Oy–**。  
  
 **\/Oy** 編譯器選項會使得偵錯工具更難使用，因為編譯器會隱藏框架指標資訊。  如果您指定偵錯編譯器選項 \([\/Z7、\/Zi、\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)\)，我們建議您在任何最佳化編譯器選項後面都指定 **\/Oy\-** 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**省略框架指標**\] 屬性。  這個屬性只會加入或移除 **\/Oy** 選項。  如果您要加入 **\/Oy\-** 選項，請按一下 \[**命令列**\] 並修改 \[**其他選項**\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)