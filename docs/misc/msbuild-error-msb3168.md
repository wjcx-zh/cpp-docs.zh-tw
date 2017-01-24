---
title: "MSBuild 錯誤 MSB3168 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
helpviewer_keywords: 
  - "MSB3168"
ms.assetid: b918c903-0030-4d87-a6ff-d8515a6f2228
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3168
**MSB3168: 重複的項目 '\<package\>' 會被忽略。**  
  
 如果您指定啟動載入器 \(Bootstrapper\) 安裝兩個完全相同的啟動載入器套件，就會發生這個警告訊息。  在這種情況下，啟動載入器只會安裝一個執行個體。  
  
### 若要更正這個錯誤  
  
-   如需 MSBuild 錯誤之原因和可能解決方案的詳細資訊，請參閱[其他資源](../Topic/Additional%20MSBuild%20Resources.md)