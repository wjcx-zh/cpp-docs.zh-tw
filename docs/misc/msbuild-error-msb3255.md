---
title: "MSBuild 錯誤 MSB3255 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3255
**MSB3255：在目標 Framework 目錄或 InstalledAssemblySubsetTables 中指定的位置找不到任何目標 Framework 子集檔案。**  
  
 當名稱傳遞至 <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A> 屬性，但找不到具有該名稱的子集時，就會發生這個錯誤。  
  
 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 是完整 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 3.5 執行階段程式庫的子集。  如需 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 的詳細資訊，請參閱[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
 程序  
  
### 若要更正這個錯誤  
  
-   將子集檔案的複本置於目標架構資料夾，或置於 <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A> 中指定的其中一個位置。  
  
## 請參閱  
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)