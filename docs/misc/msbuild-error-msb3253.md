---
title: "MSBuild 錯誤 MSB3253 | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3253
**MSB3254：專案中參考的組件 \<name\> 相依於 .NET Framework Client Profile 未包含的 \<name2\>。**  
  
 專案中參考的其中一個組件或相依組件相依於另一個組件，但該組件未包含在 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 中。  
  
 當專案參考協力廠商控制項或 DLL，而控制項或 DLL 本身參考外部組件時，通常會出現這個訊息。  例如，專案使用某個控制項，而該控制項又使用包含在完整 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 中的功能。  如果應用程式將目標重新設定為 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)]，並且安裝在沒有 [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)]的系統上，則當應用程式嘗試存取未包含在 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 子集中的功能時，可能無法正常運作。  
  
 這個「錯誤」訊息實際上只是一個警告，應用程式仍會編譯。  不過，如果控制項或 DLL 參考位於遺失的組件中的功能，稍後可能會失敗。  
  
 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 是完整 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 3.5 執行階段程式庫的子集。  如需 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 的詳細資訊，請參閱[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 若要更正這個錯誤  
  
-   從專案移除指定的組件參考，或以完整的 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 為目標，而不要以 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 子集程式庫為目標。  如需如何以完整的 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 為目標的詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
## 請參閱  
 [目標 Framework 和目標平台](../Topic/MSBuild%20Target%20Framework%20and%20Target%20Platform.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)