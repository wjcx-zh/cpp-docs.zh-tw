---
title: "MSBuild 錯誤 MSB3256 | Microsoft Docs"
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
  - "MSB3256"
ms.assetid: 809ccd0a-78cd-4bf5-83a8-2fb51815ea27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3256
**MSB3256：未從可轉散發清單讀入任何組件。  無法產生 TargetFramework 子集排除清單。**  
  
 找不到可轉散發項目的清單 \(可轉散發清單\)。  
  
 若要產生從 .NET Framework 子集排除的組件清單，需要兩個檔案：名為 FrameworkList.xml 並且包含 .NET Framework 可轉散發項目的「可轉散發清單」，和名為 client.xml 的「子集清單」，包含 .NET Framework 項目名稱。  子集定義需要這兩個清單，如果遺漏可轉散發清單，則無法以 .NET Framework 子集做為目標。  
  
 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 是完整 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 執行階段程式庫的子集。  如需 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 的詳細資訊，請參閱[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 若要更正這個錯誤  
  
-   提供名為 FrameworkList.xml 的有效可轉散發清單，或以完整的 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 可轉散發程式庫為目標。  如需如何以完整的 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 為目標的詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
## 請參閱  
 [目標 Framework 和目標平台](../Topic/MSBuild%20Target%20Framework%20and%20Target%20Platform.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)