---
title: "MSBuild 錯誤 MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4132
**MSB4132：工具版本 "'\<version\>'" 無法辨認。**  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 找不到與 `ToolsVersion` 指定值對應的工具組。  
  
### 若要更正這個錯誤  
  
-   在 project 標記或在命令列 \(使用 MSBuild **\/ToolsVersion** 參數時\)，為 `ToolsVersion` 指定有效值。  
  
## 請參閱  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)