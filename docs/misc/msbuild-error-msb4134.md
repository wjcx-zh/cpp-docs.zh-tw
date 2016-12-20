---
title: "MSBuild 錯誤 MSB4134 | Microsoft Docs"
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
  - "MSB4134"
ms.assetid: 2e4e6beb-c0c9-40ef-b75c-1c16244eba10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4134
**MSB4134: DefaultToolsVersion 不可在專案已載入引擎中之後設定。**  
  
 若在 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 建置專案之後，嘗試變更 `DefaultToolsVersion` 的值，就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
-   在建置專案之前變更 `DefaultToolsVersion` 的值。  
  
## 請參閱  
 <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>   
 <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)