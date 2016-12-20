---
title: "如何：使用視覺化檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dataviewer"
  - "vs.debug.stringviewer"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, 視覺化檢視"
  - "視覺化檢視, 關於視覺化檢視"
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "susanno"
manager: "douge"
---
# 如何：使用視覺化檢視
您可以使用視覺化檢視，以對資料類型有意義的方式，顯示變數或物件的內容。  您可以從 \[**DataTips**\]、\[**監看式**\] 視窗、\[**自動變數**\] 視窗或 \[**區域變數**\] 視窗使用視覺化檢視。  
  
 Compact Framework 上不支援視覺化檢視。  
  
> [!NOTE]
>  在**市集**應用程式中，只支援標準文字、HTML、XML 及 JSON 視覺化檢視。  不支援自訂 \(使用者建立的\) 視覺化檢視。  
  
### 若要開啟視覺化檢視  
  
1.  在 \[**DataTips**\]、\[**監看式**\] 視窗，或是在 \[**自動變數**\]、\[**區域變數**\] 或 \[**快速監看式**\] 視窗中，按一下出現在變數名稱旁邊的放大鏡圖示。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下要使用的視覺化檢視。  
  
### 若要在遠端偵錯期間使用 Managed 程式碼的視覺化檢視  
  
-   在啟動偵錯工作階段之前，將視覺化檢視 DLL 複製到遠端電腦上。  
  
     在遠端和本機電腦上，這個 DLL 的路徑必須相同。  這個路徑可以是下列其中一個位置：  
  
     *Visual Studio 安裝路徑*`\Common7\Packages\Debugger\Visualizers`  
  
     \-或\-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio 版本*`\Visualizers`  
  
## 請參閱  
 [視覺化檢視](../Topic/Create%20Custom%20Visualizers%20of%20Data.md)   
 [如何：安裝視覺化檢視](../Topic/How%20to:%20Install%20a%20Visualizer.md)   
 [如何：撰寫視覺化檢視](../Topic/How%20to:%20Write%20a%20Visualizer.md)   
 [在資料提示中檢視資料值](../Topic/View%20data%20values%20in%20Data%20Tips%20%20in%20the%20code%20editor.md)