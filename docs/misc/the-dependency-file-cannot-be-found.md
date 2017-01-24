---
title: "The dependency &#39;file&#39; cannot be found | Microsoft Docs"
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
  - "vs.tasklisterror.supdepnotfound"
ms.assetid: a0e6e658-c723-40da-8275-fa212165bd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The dependency &#39;file&#39; cannot be found
您的專案參考之一本身包含找不到的參考 \(相依性\)。  
  
 當您原始程式碼控制的專案中在登記時，您可能會發現有些相依性在您的電腦中無法解析。  這是因為參考路徑屬性 \(Property\) 是特定電腦的屬性 \(Property\)，因此不在原始程式碼控制的範圍內。  
  
### 若要更正這個錯誤  
  
1.  請在磁碟上找到指示的組件參考並修改您的 Reference Path 屬性 \(Property\)。  
  
2.  如果您在磁碟上找不到組件檔，或是如果磁碟上找不到組件相依性的話，您可能必須重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或協力廠商的自訂控制項。  並且，如果要在原始檔控制專案中登記，則可能必須安裝專案所需的協力廠商控制項。  
  
 這種情況不會阻止專案建置。  但是，執行應用程式時可能會有 TypeLoadException。  並且，將不會向部署處理報告其受影響的相依性。  
  
 您可以在 \[方案總管\] 中的 \[**參考**\] 節點內，看到您的專案參考。  
  
## 請參閱  
 [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/8e549b39-7256-456a-8fd7-089b23facf9c)