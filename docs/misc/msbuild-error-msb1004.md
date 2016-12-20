---
title: "MSBuild 錯誤 MSB1004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.MissingTargetError"
helpviewer_keywords: 
  - "MSB1004"
ms.assetid: aed36761-ab07-486c-b5eb-48ccb1c387dd
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1004
**請指定目標 \(Target\) 的名稱。**  
  
 至少要使用 **\/target** 參數指定一個目標。  
  
### 若要更正這個錯誤  
  
1.  指定一或多個目標。  您可以使用逗號或分號來分隔目標清單，例如 `/target:Clean;Compile`。  或者，重複此參數，例如 `/t:Clean /t:` `Compile`。  
  
## 請參閱  
 [目標](../Topic/MSBuild%20Targets.md)   
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)