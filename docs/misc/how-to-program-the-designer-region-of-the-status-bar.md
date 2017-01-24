---
title: "如何：程式設計狀態列的設計工具區域  | Microsoft Docs"
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
  - "設計工具區域, 狀態列"
  - "狀態列, 程式設計"
  - "狀態列, 設計工具區域"
ms.assetid: 735a86bb-80b2-4557-9677-00799856017f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 如何：程式設計狀態列的設計工具區域 
設計工具區域的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]狀態列會顯示適用於編輯，例如，行號或游標位置的資料行數目的資訊。  
  
### 到 Visual Studio 的狀態列上的設計工具區域的程式  
  
1.  取得執行個體的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>介面，可透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服務。  
  
2.  更新設計工具區域的 \[狀態列\] 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetInsMode%2A>方法以及<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetLineColChar%2A>方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>執行個體。  
  
## 範例  
 這個範例會示範如何以程式設計的狀態列上的設計工具區域。  
  
 [!code-vb[VSSDKDesignerStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-designer-region-of-the-status-bar_1.vb)]
 [!code-cs[VSSDKDesignerStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-designer-region-of-the-status-bar_1.cs)]  
  
## 請參閱  
 [擴充 \[狀態\] 列](../Topic/Extending%20the%20Status%20Bar.md)   
 [如何：讀取和寫入狀態列的意見反應區域](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：程式設計狀態列的進度列區域 ](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：使用狀態列的動畫區域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)