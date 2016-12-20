---
title: "MSBuild 錯誤 MSB3185 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3185
**MSB3185: 未指定資訊清單的 EntryPoint。**  
  
 如果資訊清單沒有指定進入點，就會產生這個錯誤訊息。  應用程式資訊清單和部署資訊清單都可能會發生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   如果使用的是 GenerateApplicationManifest 工作，請確定指定的是有效的進入點 \(Entry Point\)，或將 TargetFrameworkVersion 屬性設定為 "v3.5" \(含\) 以上。  如果是應用程式資訊清單，有效的進入點是 .exe 檔案。  
  
-   如果使用的是 GenerateDeploymentManifest 工作，請確定在資訊清單內指定了有效的進入點。  如果是部署資訊清單，則有效的進入點是應用程式資訊清單。  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)   
 [MSBuild 錯誤 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 錯誤 MSB3117](../misc/msbuild-error-msb3117.md)   
 [MSBuild 錯誤 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 錯誤 MSB3174](../misc/msbuild-error-msb3174.md)