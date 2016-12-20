---
title: "範例中所使用的服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "在範例中出現的服務"
  - "範例, 服務"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 範例中所使用的服務
中的範例[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]進行的許多服務使用。  以下列出一些常用服務和用法的範例。  
  
> [!NOTE]
>  如果參考，並不支援的範例可供使用，則會列出參考範例。  
  
|服務|範例|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[如何︰ 使用活動記錄檔](../Topic/How%20to:%20Use%20the%20Activity%20Log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|已取代。  請改用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|Reference.HelpIntegration 範例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|SingleViewEditor 範例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|SingleViewEditor 範例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package、 Reference.ToolWindow，以及許多其他範例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|SingleViewEditor 範例。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package、 Reference.ToolWindow，以及許多其他範例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt，BscPrj，FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor，BscPrj，FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow、 BscEdit，以及許多其他範例|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## 請參閱  
 [可用服務清單](../Topic/List%20of%20Available%20Services.md)   
 [服務的基本資訊](../Topic/Service%20Essentials.md)