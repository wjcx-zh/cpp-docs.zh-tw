---
title: "如何：使用狀態列的動畫區域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "狀態列, 程式設計"
  - "狀態列, 動畫區域"
  - "動畫區域, 狀態列"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：使用狀態列的動畫區域
動畫 \(地區\) 的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] ，狀態列會顯示重複循環的動畫，指示漫長的作業或不定長度的作業 \(例如，建置多個專案的方案\)。  
  
### 若要使用 Visual Studio 的狀態列上的動畫區域  
  
1.  取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面，可透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
2.  啟動動畫，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A>的狀態列上的方法。  傳入做的第一個參數，以及動畫圖示做為第二個參數值的參考值為 1。  
  
3.  停止動畫，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A>的狀態列上的方法。  傳入做的第一個參數，並做為第二個參數值的動畫圖示的參考值為 0。  
  
## 範例  
 這個範例會示範如何執行動畫區域中的內建的動畫。  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## 請參閱  
 [擴充 \[狀態\] 列](../Topic/Extending%20the%20Status%20Bar.md)   
 [如何：讀取和寫入狀態列的意見反應區域](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：程式設計狀態列的進度列區域 ](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：程式設計狀態列的設計工具區域 ](../misc/how-to-program-the-designer-region-of-the-status-bar.md)