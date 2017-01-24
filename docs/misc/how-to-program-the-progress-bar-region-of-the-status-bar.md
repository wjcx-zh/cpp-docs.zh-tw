---
title: "如何：程式設計狀態列的進度列區域  | Microsoft Docs"
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
  - "狀態列. 進度列區域"
  - "進度列, 狀態列"
  - "狀態列,  程式設計"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 如何：程式設計狀態列的進度列區域 
進度列區域的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] ，狀態列會顯示快速作業，例如，將檔案儲存至磁碟的增加進度。  
  
### 若要使用 Visual Studio 的狀態列上的進度列區域  
  
1.  取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面，可透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
2.  初始化進度列，開始值，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A>方法。  
  
3.  更新進度列，您的作業進行時使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A>方法，以設定新的值。  
  
## 範例  
 本範例將示範如何初始化，並更新進度列。  
  
 [!code-cs[VSSDKProgressStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-progress-bar-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKProgressStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-progress-bar-region-of-the-status-bar_1.vb)]  
  
 在範例中，程式碼：  
  
-   取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面從<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
-   初始化進度列，以指定起始值，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A>方法。  
  
-   逐一查看，以模擬作業`for`迴圈，並更新進度列的值，藉由使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A>方法。  
  
-   藉由清除進度列<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A>方法。  
  
## 請參閱  
 [擴充 \[狀態\] 列](../Topic/Extending%20the%20Status%20Bar.md)   
 [如何：讀取和寫入狀態列的意見反應區域](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：使用狀態列的動畫區域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [如何：程式設計狀態列的設計工具區域 ](../misc/how-to-program-the-designer-region-of-the-status-bar.md)