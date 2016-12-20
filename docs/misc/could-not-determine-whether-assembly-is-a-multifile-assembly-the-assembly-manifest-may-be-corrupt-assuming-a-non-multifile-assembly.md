---
title: "無法決定 &#39;assembly&#39; 是否為多檔案組件。 組件資訊清單可能已損毀。 假設為非多檔案組件。 | Microsoft Docs"
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
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法決定 &#39;assembly&#39; 是否為多檔案組件。 組件資訊清單可能已損毀。 假設為非多檔案組件。
專案系統無法讀取專案所參考的組件，因此專案系統無法判斷您是否參考多檔案組件。 因此，組件可能不會正確複製到輸出目錄。  
  
 **更正這個錯誤**  
  
-   重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \(若組件隨附 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或 .NET Framework\)。  
  
     \-或\-  
  
-   重新安裝適當的協力廠商控制項。  
  
     此錯誤不會防止建置專案。 不過，可能會發生執行階段錯誤。  
  
## 請參閱  
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/zh-tw/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)