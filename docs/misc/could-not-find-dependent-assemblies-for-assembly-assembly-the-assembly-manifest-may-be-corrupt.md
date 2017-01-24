---
title: "找不到組件 &#39;assembly&#39; 的相依組件。 組件資訊清單可能已損毀。 | Microsoft Docs"
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
  - "vs.tasklisterror.cannotfinddependencies"
ms.assetid: 6d6e6dda-6cec-49d0-9659-63dfdbd7d247
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 找不到組件 &#39;assembly&#39; 的相依組件。 組件資訊清單可能已損毀。
專案系統無法讀取專案所參考的組件，因此專案系統無法判斷組件的相依性。 此錯誤不會防止建置專案。 不過，可能會發生執行階段錯誤。  
  
 **更正這個錯誤**  
  
-   重新安裝 Visual Studio \(如果組件隨附 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)]\)。  
  
     \-或\-  
  
-   重新安裝適當的協力廠商控制項。  
  
## 請參閱  
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)