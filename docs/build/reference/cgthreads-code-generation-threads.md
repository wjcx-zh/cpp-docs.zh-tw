---
title: "/cgthreads (程式碼產生執行緒) | Microsoft Docs"
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
  - "/cgthreads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/cgthreads 編譯器選項 (C++)"
  - "cgthreads"
  - "cgthreads 編譯器選項 (C++)"
  - "-cgthreads 編譯器選項 (C++)"
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /cgthreads (程式碼產生執行緒)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 cl.exe 執行緒的數目，以用於最佳化及程式碼產生。  
  
## 語法  
  
```  
/cgthreads[1-8]  
```  
  
## 引數  
 數字  
 cl.exe 要使用的執行緒最大數目範圍為 1 到 8。  
  
## 備註  
 **\/cgthreads** 選項會指定 cl.exe 平行用於編譯最佳化及程式碼產生階段的執行緒最大數目。  請注意，**\/cgthreads** 與 `number` 引數之間可以沒有空格。  根據預設，cl.exe 會使用四個執行緒，就像已指定 **\/cgthreads4** 一樣。  如果可以使用更多處理器核心，則較大的 `number` 值可以改善建置時間。  當此選項與 [\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md) 合併使用時尤其有用。  
  
 針對建置可以指定多個層級的平行處理原則。  msbuild.exe 參數 **\/maxcpucount** 會指定可以平行執行的 MSBuild 處理程序數目。  [\/MP \(使用多處理序建置\)](../../build/reference/mp-build-with-multiple-processes.md) 編譯器旗標會指定可同時編譯原始檔的 cl.exe 處理程序數目。  **\/cgthreads** 選項會指定每一個 cl.exe 處理程序所使用的執行緒數目。  由於處理器可同時執行的執行緒數目最多只能與處理器核心數目相同，因此同時針對所有這些選項指定較大的值不僅沒有什麼用處，反而可能適得其反。  如需如何平行建置專案的詳細資訊，請參閱[同時建置多個專案](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[配置屬性\]、\[C\/C\+\+\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[其他選項\] 屬性，以包括 **\/cgthreads**`N`，其中 `N` 為 1 到 8 的值，然後選取 \[確定\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)