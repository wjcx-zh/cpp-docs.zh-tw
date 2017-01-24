---
title: "MSBuild 錯誤 MSB1016 | Microsoft Docs"
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
  - "MSBuild.MissingVerbosityError"
helpviewer_keywords: 
  - "MSB1016"
ms.assetid: 967a9757-0513-48ae-bf1d-b1b019993c70
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1016
**請指定詳細等級。**  
  
 **\/verbosity** 參數必須指定詳細等級。  
  
### 若要更正這個錯誤  
  
1.  使用 `/verbosity:<level>` 格式來指定詳細等級。  可用的詳細等級為：q\[uiet\] \(無訊息\)、m\[inimal\] \(最小\)、n\[ormal\] \(一般\)、d\[etailed\] \(詳細\) 和 diag\[nostic\] \(診斷\)，例如，`/verbosity:quiet`、 `/verbosity:q` 或  `/v:q`。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)