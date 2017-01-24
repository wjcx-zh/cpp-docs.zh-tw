---
title: "專案目標 Framework 未安裝對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 專案目標 Framework 未安裝對話方塊
您已經開啟專案，但該專案選定您的電腦未安裝的架構。 若要繼續，您必須在此對話方塊中選取其中一個選項。  
  
> [!NOTE]
>  每當您下載及安裝新架構時，您必須重新啟動 Visual Studio。  
  
## Visual Basic 和 C\#  
 如果您開啟 Visual Basic 或 Visual C\# 專案，請選取下列選項之一。  
  
 **變更目標為 .NET Framework 4.5。您稍後可以變更回 .NET Framework** *版本***。**  
 將專案重定為 .NET Framework 4.5。 您稍後可以重新安裝舊版，然後重新設定專案的目標。  
  
 **下載適用於.NET Framework \<Version\> 的目標組件。專案不會變更。**  
 開啟 Microsoft 下載中心網站，您可以在其中下載您想要的 .NET Framework 版本。 您的專案是從方案中卸載。 下載並安裝所需的架構之後，您必須重新啟動 Visual Studio，然後重新開啟專案。  
  
 **不要載入專案。**  
 維持從方案中卸載專案。 您稍後可以安裝所需的架構，然後重新載入專案。  
  
## Visual C\+\+  
 如果您開啟 Visual C\+\+ 專案，請選取下列選項之一。  
  
 **下載適用於.NET Framework**  *Version* **的目標組件。專案不會變更。**  
 開啟 Microsoft 下載中心網站，您可以在其中下載您想要的 .NET Framework 版本。 下載完成後，您的專案被重新指向該版本。 您的專案是從方案中卸載。 下載並安裝所需的架構之後，您必須重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，然後重新開啟專案。  
  
 **不要載入專案。**  
 維持從方案中卸載專案。 您稍後可以安裝所需的架構，然後重新載入專案。  
  
## 請參閱  
 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)   
 [疑難排解 .NET Framework 目標錯誤](../Topic/Troubleshooting%20.NET%20Framework%20Targeting%20Errors.md)   
 [加入參考](../ide/adding-references-in-visual-cpp-projects.md)