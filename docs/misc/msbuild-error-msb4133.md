---
title: "MSBuild 錯誤 MSB4133 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4133
**MSB4133：已指定預設工具版本 "\<x.x.\>"，但是找不到它的定義。**  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 找不到專案檔中定義為 `DefaultToolsVersion` 的工具組。  
  
### 若要更正這個錯誤  
  
-   確定正確指定 `DefaultToolsVersion`，而且此工具組已在登錄或 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 組態檔中定義。  
  
## 請參閱  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)