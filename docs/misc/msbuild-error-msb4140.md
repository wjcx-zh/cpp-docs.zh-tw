---
title: "MSBuild 錯誤 MSB4140 | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4140
**MSB4140: 指定的預設工具版本不在登錄中，也不在組態檔中。**  
  
 專案沒有指定預設 `ToolsVersion` 值。  因此，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 不知道要使用哪一個值。  
  
### 若要更正這個錯誤  
  
-   確定在登錄中定義工具組的位置或在組態檔 \(例如 msbuild.exe.config\) 中，已指定 `DefaultToolsVersion` 值。  
  
## 請參閱  
 [標準和自訂工具組的組態](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)