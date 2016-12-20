---
title: "MSBuild 錯誤 MSB3023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3023
**未指定複製的目的地。  請提供 "'\<attribute\>'" 或 "'\<attribute\>'"。**  
  
 必須使用其中一個 `DestinationFiles` 和 `DestinationDirectory` 工作屬性，來指定 `Copy` 工作的目的端。  
  
### 若要更正這個錯誤  
  
-   為 `Copy` 工作指定 `DestinationFiles` 或 `DestinationDirectory`。  
  
## 請參閱  
 [Copy Task](../Topic/Copy%20Task.md)   
 [工作](../Topic/MSBuild%20Tasks.md)