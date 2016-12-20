---
title: "將 Web 服務加入專案系統中 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案系統, 加入 Web 服務"
  - "Web 服務, 加入 VSPackage 專案系統中"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 將 Web 服務加入專案系統中
XML Web 服務在一般情況下，是 URL 可定址回到專案系統使用 SOAP \(簡易物件存取通訊協定\) 通訊協定的程式化的資訊的資源。  您可以藉由使用 Web 服務兩者整合以 VSPackage 專案系統<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>介面。  
  
### 若要將 Web 服務加入至您的專案系統  
  
1.  呼叫`QueryService`的<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>介面透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>服務。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法。  如果您傳入`pDiscoverySession`參數則做為`NULL`、 探索工作階段時建立，以及工作階段就會快取，使其可供後續使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>介面。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>方法會傳回變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>。  
  
3.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 方法。  自動化物件傳入作為 Web 服務參考\] 資料夾的`pUnkWebReferenceFolder`參數。  Visual Studio 環境接著會檢查 Web 服務是否已經存在。  如果 Web 服務不存在，環境就會下載，並將 Web 服務加入至把資料夾及其中的任何其他檔案 \(例如.wsdl 檔案\) 到資料夾的子節點。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>