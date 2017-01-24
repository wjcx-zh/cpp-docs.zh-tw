---
title: "MSBuild 錯誤 MSB4135 | Microsoft Docs"
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
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB4135
**MSB4135: 從登錄機碼 "'\<key\>'" 或子機碼讀取工具組資訊時發生錯誤'  \<key\>'**  
  
 無法讀取登錄中定義的自訂工具組資訊。  
  
### 若要更正這個錯誤  
  
-   如果您在登錄中定義了自訂工具組，請確定它的登錄格式有效，也就是有正確的 `ToolsVersion` 名稱以及正確的 `MSBuildBinPath` 或 `MSBuildToolsPath` 值。  
  
## 請參閱  
 [標準和自訂工具組的組態](../Topic/Standard%20and%20Custom%20Toolset%20Configurations.md)   
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)