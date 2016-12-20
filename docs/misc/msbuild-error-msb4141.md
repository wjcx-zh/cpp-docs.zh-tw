---
title: "MSBuild 錯誤 MSB4141 | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4141
**MSB4141: 未針對 ToolsVersion "\<x.x\>" 指定 MSBuildToolsPath。**  
  
 定義了自訂工具組，但沒有定義 `MSBuildToolsPath` 的值。  
  
### 若要更正這個錯誤  
  
-   在登錄或 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 組態檔中定義自訂工具組時，為 `MSBuildToolsPath` 指定有效值。  
  
## 請參閱  
 [標準和自訂工具組的組態](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)