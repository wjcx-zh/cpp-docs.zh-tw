---
title: "MSBuild 錯誤 MSB3174 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidValue"
helpviewer_keywords: 
  - "MSB3174"
ms.assetid: 6f9a040c-7f21-40fd-bf74-03f99f265e79
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3174
**MSB3174: '\<file\>' 的值無效。**  
  
 如果建置處理序在檢查資訊清單檔的格式時遇到了一般性的問題，就會產生這個錯誤訊息。  這個錯誤訊息會指出資訊清單檔的名稱。  
  
 下列任一參數如果設定不正確，就會產生這個錯誤訊息。  列出的每一個參數都是 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> 或 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest> 屬性，例如 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> 或 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>。  
  
 當工作為 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>，適用下列需求：  
  
|參數|需求|  
|--------|--------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|必須是有效的檔案名稱。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|其需求與 <xref:System.Version.%23ctor%2A> 相同。  所有的八位元資料都必須大於 0。  必須指定所有 \(共四個\) 的八位元資料。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ClrVersion%2A>|其需求與 <xref:System.Version.%23ctor%2A> 相同。  所有的八位元資料都必須大於 0。  必須指定所有 \(共四個\) 的八位元資料。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.OSVersion%2A>|其需求與 <xref:System.Version.%23ctor%2A> 相同。  所有的八位元資料都必須大於 0。  必須指定所有 \(共四個\) 的八位元資料。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|必須是 **AnyCPU**、**x86**、**x64** 或 **Itanium**。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.ManifestType%2A>|必須是 **Native** 或 **ClickOnce**。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|可以是空字串。  也可以是中性文化特性 \(由兩個小寫字母的語言代碼所指定，例如 "jp" 代表日本\)。  否則，這個值和 <xref:System.Globalization.CultureInfo.%23ctor%2A> 的需求相同。|  
|<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>|格式必須為 v*\#*.*\#*。  必須為 2.0 以後的版本。  可接受空字串。|  
  
 當工作為 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>，適用下列需求：  
  
|參數|需求|  
|--------|--------|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyName%2A>|必須是有效的檔案名稱。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.AssemblyVersion%2A>|其需求與 <xref:System.Version.%23ctor%2A> 相同。  所有的八位元資料都必須大於 0。  必須指定所有 \(共四個\) 的八位元資料。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.MinimumRequiredVersion%2A>|其需求與 <xref:System.Version.%23ctor%2A> 相同。  所有的八位元資料都必須大於 0。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.Platform%2A>|必須是 **AnyCPU**、**x86**、**x64** 或 **Itanium**。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateManifestBase.TargetCulture%2A>|可以是空字串。  也可以是中性文化特性 \(由兩個小寫字母的語言代碼所指定，例如 "jp" 代表日本\)。  否則，這個值和 <xref:System.Globalization.CultureInfo.%23ctor%2A> 的需求相同。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateMode%2A>|必須為 **Foreground** 或 **Background**。  可接受空字串。|  
|<xref:Microsoft.Build.Tasks.GenerateDeploymentManifest.UpdateUnit%2A>|必須是 **Hours**、**Days** 或 **Weeks**。  可接受空字串。|  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild 錯誤 MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild 錯誤 MSB3117](../misc/msbuild-error-msb3117.md)   
 [MSBuild 錯誤 MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild 錯誤 MSB3185](../misc/msbuild-error-msb3185.md)