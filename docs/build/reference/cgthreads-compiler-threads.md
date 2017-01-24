---
title: "/CGTHREADS (編譯器執行緒) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CGTHREADS 連結器選項"
  - "CGTHREADS 連結器選項"
  - "-CGTHREADS 連結器選項"
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CGTHREADS (編譯器執行緒)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定在指定連結時間程式碼產生時要用於最佳化和程式碼產生的 cl.exe 執行緒數目。  
  
## 語法  
  
```  
/CGTHREADS:[1-8]  
```  
  
## 引數  
 數字  
 cl.exe 要使用的執行緒數目上限，範圍在 1 到 8 之間。  
  
## 備註  
 **\/CGTHREADS** 選項指定當指定連結時間程式碼產生 \([\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)\) 時，cl.exe 並行用於編譯的最佳化和程式碼產生階段的執行緒數目上限。  cl.exe 預設會使用四個執行緒，如同指定了 **\/CGTHREADS:4** 一樣。  如果可以使用更多處理器核心，較大的 `number` 值可以改善建置時間。  
  
 可以為組建指定多個平行處理層級。  msbuild.exe 參數 **\/maxcpucount** 會指定可以平行執行的 MSBuild 處理序數目。  [\/MP \(使用多處理序建置\)](../../build/reference/mp-build-with-multiple-processes.md) 編譯器旗標會指定同時編譯原始程式檔的 cl.exe 處理序數目。  [\/cgthreads](../../build/reference/cgthreads-code-generation-threads.md) 編譯器選項會指定每個 cl.exe 處理序使用的執行緒數目。  由於處理器可同時執行的執行緒數目最多只能與處理器核心數目相同，因此同時針對所有這些選項指定較大的值不僅沒有什麼用處，反而可能適得其反。  如需如何平行建置專案的詳細資訊，請參閱[同時建置多個專案](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md)。  
  
### 在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[組態屬性\]、\[連結器\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  將 \[其他選項\] 屬性修改成包含 **\/CGTHREADS:**`number`，其中 `number` 是從 1 到 8 的值，然後選擇 \[確定\]。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [連結器選項](../../build/reference/linker-options.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)