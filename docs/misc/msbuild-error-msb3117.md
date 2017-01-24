---
title: "MSBuild 錯誤 MSB3117 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3117"
ms.assetid: 18aec642-6000-4626-bf75-f3547769c780
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3117
**MSB3117: 應用程式設定為裝載在瀏覽器中，但 TargetFrameworkVersion 是設定為 2.0 版。**  
  
 部署的 WPF Web 瀏覽器應用程式之 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> 屬性設定為 `True`，但 TargetFrameworkVersion 設定為 `v2.0` 或 `v3.0`。  如果您使用這個設定，也必須將 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 屬性值設定為 `v3.5` 或更高。  
  
### 若要更正這個錯誤  
  
-   將 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 屬性值設定為 `v3.5` 或更高。  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild 錯誤 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 錯誤 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 錯誤 MSB3174](../misc/msbuild-error-msb3174.md)   
 [MSBuild 錯誤 MSB3185](../misc/msbuild-error-msb3185.md)