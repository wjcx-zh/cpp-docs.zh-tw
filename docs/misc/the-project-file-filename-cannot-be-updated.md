---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
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
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
您正在嘗試開啟由較早版本之 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 建立的專案。  專案必須升級到目前的格式，但由於指定的專案檔 \(.vbproj\) 標示為唯讀，或檔案是在來源控制下且目前由其他使用者鎖定，因而無法更新。  
  
### 若要更正這個錯誤  
  
1.  在檔案總管中，找出指定的專案檔。  
  
2.  在 \[**檔案**\] 功能表上，選擇 \[**屬性**\]。  
  
3.  在 \[**屬性**\] \(Properties\) 對話方塊中，取消核取 \[**唯讀**\] 屬性 \(Attribute\)。  
  
 如果程式碼是在原始程式碼控制下，並由其他使用者鎖定，請等待檔案可供使用時，再從本機查看檔案。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)