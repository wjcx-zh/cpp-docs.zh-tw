---
title: "MSBuild 錯誤 MSB1018 | Microsoft Docs"
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
  - "MSBuild.InvalidVerbosityError"
helpviewer_keywords: 
  - "MSB1018"
ms.assetid: fb4deacc-a799-44e8-8980-d70d9da4caa1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1018
**詳細等級無效。**  
  
 指定的詳細等級不是其中一個可用的詳細等級。  
  
### 若要更正這個錯誤  
  
1.  檢查詳細等級的拼字是否正確。  可用的詳細等級為：q\[uiet\] \(無訊息\)、m\[inimal\] \(最小\)、n\[ormal\] \(一般\)、d\[etailed\] \(詳細\) 和 diag\[nostic\] \(診斷\)，例如，`/verbosity:quiet`、 `/verbosity:q` 或  `/v:q`。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)   
 [組建記錄器](../Topic/Build%20Loggers.md)