---
title: "HLSL 屬性頁：一般 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.FXCompilerTool.ShaderModel"
  - "VC.Project.FXCompilerTool.PreprocessorDefinitions"
  - "VC.Project.FXCompilerTool.ShaderType"
  - "VC.Project.FXCompilerTool.EnableDebuggingInformation"
  - "VC.Project.FXCompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.FXCompilerTool.DisableOptimizations"
  - "VC.Project.FXCompilerTool.EntryPointName"
dev_langs: 
  - "C++"
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: 8
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 8
---
# HLSL 屬性頁：一般
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要設定 HLSL 編譯器 \(fxc.exe\) 的下列屬性，請使用它的 \[**概觀**\] 屬性頁。  如需如何以 HLSL 存取資料夾的 \[**概觀**\] 屬性頁的詳細資訊，請參閱 [如何：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
## UIElement 清單  
 \[**其他 Include 目錄**\]  
 將一個或多個目錄加入至 Include 路徑。  使用分號分隔目錄。  
  
 這個屬性對應至 **\/I\[path\]** 命令列引數。  
  
 \[**Entrypoint 名稱**\]  
 為著色器的進入點。  根據預設，值是 \[**主要**\]。  
  
 這個屬性對應至 **\/E\[name\]** 命令列引數。  
  
 \[**停用最佳化**\]  
 停用最佳化的 \[**是 \(\/Od\)**\] ;否則， \[**否則**\]。  根據預設，值是 \[**偵錯**\] 組態和 \[**否則**\] 的 \[**是 \(\/Od\)**\] \[**版本**\] 組態的。  
  
 對 HLSL 編譯器的 **\/Od** 命令列引數隱含套用 **\/Gfp** 命令列引數，不過，輸出不可以與是透過明確透過 **\/Od** 和 **\/Gfp** 命令列引數所產生的輸出。  
  
 \[**啟用偵錯資訊**\]  
 啟用偵錯資訊的 \[**是 \(\/Zi\)**\] ;否則， \[**否則**\]。  根據預設，值是 \[**偵錯**\] 組態和 \[**否則**\] 的 \[**是 \(\/Zi\)**\] \[**版本**\] 組態的。  
  
 \[**著色器類型**\]  
 指定要著色器。  各種圖形管線的著色器實作不同的組件。  某些著色器只能在 \[**著色器模型**\] 屬性指定\) 的最近著色器模型 \(—例如，計算著色器中引入了在著色器模型 5。  
  
 這個屬性對應至 **\/T \[type\]\_\[model\]** 命令列引數的 **\[type\]** 部分需 HLSL 編譯器。  \[**著色器模型**\] 屬性指定引數的 **\[model\]** 區段。  
  
 \[**著色器模型**\]  
 指定著色器模型。  不同的著色器模型有不同的功能。  一般而言，最近著色器模型提供擴充功能，但是需要更現代圖形硬體執行著色器程式碼。  由 \[**著色器類型**\] 屬性指定\) 的某些著色器 \(只能在最近著色器模型。例如，計算著色器中引入了在著色器模型 5。  
  
 這個屬性對應至 **\/T \[type\]\_\[model\]** 命令列引數的 **\[model\]** 部分需 HLSL 編譯器。  \[**著色器類型**\] 屬性指定引數的 **\[type\]** 區段。  
  
 **前置處理器定義**  
 將一或多個前置處理器符號定義加入套用至 HLSL 原始程式碼檔案。  使用分號來分隔符號定義。  
  
 這個屬性對應至 **\/D \[definitions\]** 命令列引數於 HLSL 編譯器。  
  
## 請參閱  
 [HLSL 屬性頁](../ide/hlsl-property-pages.md)   
 [HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)   
 [HLSL 屬性頁：輸出檔](../ide/hlsl-property-pages-output-files.md)