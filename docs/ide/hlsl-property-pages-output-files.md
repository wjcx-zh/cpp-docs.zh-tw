---
title: "HLSL 屬性頁：輸出檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.FXCompilerTool.AssemblerOutput"
  - "VC.Project.FXCompilerTool.ObjectFileOutput"
  - "VC.Project.FXCompilerTool.HeaderFileOutput"
  - "VC.Project.FXCompilerTool.VariableName"
  - "VC.Project.FXCompilerTool.AssemblerOutputFile"
dev_langs: 
  - "C++"
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: 5
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 5
---
# HLSL 屬性頁：輸出檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要設定 HLSL 編譯器 \(fxc.exe\) 的下列屬性，請使用它的 \[**輸出檔**\] 屬性。  如需如何以 HLSL 存取資料夾的 \[**輸出檔**\] 屬性頁的詳細資訊，請參閱 [如何：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
## UIElement 清單  
 \[**標題變數名稱。**\]  
 指定用於編碼 HLSL 目的碼陣列的名稱。  陣列以 HLSL 編譯器輸出的標頭檔中。  標頭檔的名稱是 \[**標頭檔的名稱。**\] 屬性指定。  
  
 這個屬性對應至 **\/Vn\[name\]** 命令列引數。  
  
 \[**標頭檔的名稱。**\]  
 指定 HLSL 編譯器輸出標頭檔的名稱。  標頭包含輸入陣列 HLSL 物件程式碼。  陣列的名稱是 \[**標題變數名稱。**\] 屬性指定。  
  
 這個屬性對應至 **\/Fh\[name\]** 命令列引數。  
  
 \[**物件檔案名稱**\]  
 指定 HLSL 編譯器輸出目的檔的名稱。  根據預設，值是 \[**$ \(OutDir\) % \(檔名\) .cso**\]。  
  
 這個屬性對應至 **\/Fo\[name\]** 命令列引數。  
  
 \[**組合語言輸出**\]  
 輸出組合語言的陳述式的 \[**組件目錄 \(\/Fc\)**\] 。  輸出兩個組合語言的陳述式和對應的作業程式碼的 \[**組譯程式碼和六 \(\/Fx\)**\] 在十六位元。  根據預設，沒有輸出目錄。  
  
 \[**組合語言輸出檔**\]  
 指定 HLSL 編譯器輸出組合列表檔案的名稱。  
  
 這個屬性對應於 **\/Fc\[name\]** 和 **\/Fx \[name\]** 命令列引數。  
  
## 請參閱  
 [HLSL 屬性頁](../ide/hlsl-property-pages.md)   
 [HLSL 屬性頁：一般](../ide/hlsl-property-pages-general.md)   
 [HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)