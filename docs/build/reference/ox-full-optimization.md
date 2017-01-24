---
title: "/Ox (完全最佳化) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.ToolOptimization"
  - "/ox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ox 編譯器選項 [C++]"
  - "快程式碼"
  - "完全最佳化"
  - "Ox 編譯器選項 [C++]"
  - "-Ox 編譯器選項 [C++]"
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ox (完全最佳化)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/Ox** 編譯器選項會優先考量執行速度而非檔案大小，因而產生程式碼。  
  
## 語法  
  
```  
/Ox  
```  
  
## 備註  
 指定 **\/Ox** 編譯器選項的效果與使用下列選項相同：  
  
-   [\/Ob \(內嵌函式展開\)](../../build/reference/ob-inline-function-expansion.md)，其中選項參數是 2 \(**\/Ob2**\)。  
  
-   [\/Og \(全域最佳化\)](../../build/reference/og-global-optimizations.md)  
  
-   [\/Oi \(產生內建函式\)](../../build/reference/oi-generate-intrinsic-functions.md)  
  
-   [\/Ot \(偏好快的程式碼\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)  
  
-   [\/Oy \(框架指標省略\)](../../build/reference/oy-frame-pointer-omission.md)  
  
 **\/Ox** 是與下列各項互斥：  
  
-   [\/O1 \(降低大小\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/O2 \(最大化速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/Od \(停用 \(偵錯\)\)](../../build/reference/od-disable-debug.md)  
  
 **\/Ox** 編譯器選項也會啟用「具名傳回值」最佳化，以排除堆疊式傳回值的複製建構函式和解構函式，  如需詳細資訊，請參閱[\/O1、\/O2 \(最小大小、最快速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
 如果指定 **\/Oxs** 則可取消 **\/Ox** 編譯器選項，前者結合了 **\/Ox** 編譯器選項以及 [\/Os \(偏好小的程式碼\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)。  結合選項有利於產生較小的程式碼大小。  
  
 通常，指定 [\/O2 \(最大化速度\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 可取代 **\/Ox**、指定 [\/O1 \(降低大小\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 可取代 **\/Oxs**。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**最佳化**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)