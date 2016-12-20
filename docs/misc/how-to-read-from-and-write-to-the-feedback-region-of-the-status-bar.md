---
title: "如何：讀取和寫入狀態列的意見反應區域 | Microsoft Docs"
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
  - "意見反應區域, 狀態列"
  - "狀態列, 意見反應區域"
  - "狀態列,概觀"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 如何：讀取和寫入狀態列的意見反應區域
意見反應 \(地區\) 的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]狀態列顯示文字。  您可以設定和擷取文字、 顯示靜態文字，並反白顯示的文字。  
  
### 若要使用 Visual Studio 的狀態列上的意見反應區域  
  
1.  取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面，可透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
2.  決定狀態列是否已凍結藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A>方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>執行個體。  
  
3.  設定意見反應區域的文字，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A>方法，並將文字字串中的傳遞。  
  
4.  讀取的意見反應區域的文字，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A>方法。  
  
## 範例  
 這個範例會示範如何撰寫文字，並讀取 \[意見反應\] 區域中的文字。  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 在上述範例中，程式碼會執行下列操作：  
  
-   取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面從<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
-   檢查如果狀態列上會凍結藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A>方法。  
  
-   \[狀態\] 列來禁止做進一步的更新，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A>方法。  
  
-   讀取 \[狀態列\] 中的文字，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A>方法並將其顯示在訊息方塊。  
  
-   允許狀態列上的更新，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> ，以及將 0 傳遞參數中。  
  
-   清除 \[狀態列\] 的內容，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A>方法。  
  
## 請參閱  
 [擴充 \[狀態\] 列](../Topic/Extending%20the%20Status%20Bar.md)   
 [如何：程式設計狀態列的進度列區域 ](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：使用狀態列的動畫區域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [如何：程式設計狀態列的設計工具區域 ](../misc/how-to-program-the-designer-region-of-the-status-bar.md)