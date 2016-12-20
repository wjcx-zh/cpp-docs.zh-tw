---
title: "MSBuild 錯誤 MSB3118 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3118
**MSB3118: 應用程式設定為使用應用程式信任，但是 TargetFrameworkVersion 不是 3.5 版。**  
  
 當您將 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> 屬性設定為 `True`、<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 屬性設定為低於 `v3.5` 的版本 \(例如，`v2.0`\) 時，就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
-   將 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 屬性設定為 `v3.5` 或更高。  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild 錯誤 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 錯誤 MSB3117](../misc/msbuild-error-msb3117.md)   
 [MSBuild 錯誤 MSB3119](../misc/msbuild-error-msb3119.md)   
 [MSBuild 錯誤 MSB3174](../misc/msbuild-error-msb3174.md)   
 [MSBuild 錯誤 MSB3185](../misc/msbuild-error-msb3185.md)