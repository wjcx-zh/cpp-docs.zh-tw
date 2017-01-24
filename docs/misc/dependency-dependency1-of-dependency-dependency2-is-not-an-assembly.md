---
title: "相依性 &#39;dependency2&#39; 的相依性 &#39;dependency1&#39; 不是組件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.notcomplusassembly2"
ms.assetid: e3b96601-458e-40de-81ea-ddcae9b42996
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 相依性 &#39;dependency2&#39; 的相依性 &#39;dependency1&#39; 不是組件
專案系統判定組件 \(dependency2\) 的特定相依性 \(dependency1\) 不是 .NET 組件。  
  
 **更正這個錯誤**  
  
-   重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \(若組件隨附 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或 .NET Framework\)。  
  
     \-或\-  
  
-   重新安裝適當的協力廠商控制項。  
  
     此錯誤不會防止建置專案。 不過，可能會發生執行階段錯誤。  
  
## 請參閱  
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)