---
title: "MSBuild 錯誤 MSB4142 | Microsoft Docs"
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
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4142
**MSB4142: 對於 ToolsVersion "\<x.x\>"，MSBuildToolsPath 與 MSBuildBinPath 不相同。**  
  
 工具組定義在 `MSBuildBinPath` 和 `MSBuildToolsPath` 指定了不同的值。  
  
### 若要更正這個錯誤  
  
-   確定在工具組定義中，`MSBuildBinPath` 與 `MSBuildToolsPath` 相同。  
  
## 請參閱  
 [標準和自訂工具組的組態](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)