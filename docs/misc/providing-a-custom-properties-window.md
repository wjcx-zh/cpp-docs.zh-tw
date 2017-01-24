---
title: "提供自訂屬性視窗 | Microsoft Docs"
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
  - "屬性瀏覽器, 提供"
  - "屬性視窗, 提供您自已的"
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 提供自訂屬性視窗
它也可以提供您自己**屬性**視窗對於指定的專案系統，而不是擴充的**屬性**視窗所提供的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  最常遇到的情形是當您自行實作設置在視窗框架的物件。  
  
 萬一您不會實作設置在視窗框架，該物件，但仍能存取它以其他方式，有許多方法來存取<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>在此頁面上的最後一個程序中所示的介面。  
  
### 若要提供您的 \[屬性\] 視窗  
  
1.  定義 GUID，表示您**屬性** \] 視窗的實作。  
  
2.  在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作中，使用<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>到 proffer 服務您**屬性** Visual Studio 環境的服務\] 視窗。  
  
### 若要呼叫您的 \[屬性\] 視窗  
  
1.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
2.  `QueryService`對於<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>的<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>方法。  
  
3.  取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>的<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>第一個參數設定為`SEID_PropertyBrowserSID` \(取自<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列舉型別\)，及第三個參數， `varValue`，代表一種字串形式的 GUID，表示您**屬性**視窗。  在第一個建立進行這項呼叫一次您**屬性** \] 視窗的文件視窗。  在呼叫之後這**屬性** \] 視窗是您的視窗框架相關聯。  
  
### 取得視窗框架物件，當您不是實作器  
  
-   您可以`QueryService`的<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務從<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>與參數一起`propid`設定為 \[ <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。  
  
-   您可以取得使用中文件視窗，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>到 SVsMonitorSelection 服務。  設定參數， `elementid`到`SEID_WindowFrame`、 從<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列舉型別。  
  
## 請參閱  
 [擴充屬性](../Topic/Extending%20Properties.md)   
 [屬性視窗中的欄位和介面](../Topic/Properties%20Window%20Fields%20and%20Interfaces.md)