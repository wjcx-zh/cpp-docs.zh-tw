---
title: "MSBuild 錯誤 MSB3116 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3116
**MSB3116: 應用程式標記為裝載在瀏覽器中，但也標記為線上及離線使用。  請將您的應用程式變更為只能線上使用。**  
  
 部署 WPF Web 瀏覽器應用程式時，必須將 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> 屬性設定為 `True`。  當 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> 設定為 `True` 時，您必須將 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> 屬性設定為 `False` \(只能線上安裝\)。  如果不符合第二個條件，就會收到這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   將 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> 屬性設定為 `False`。  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)