---
title: "MSBuild 錯誤 MSB1002 | Microsoft Docs"
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
  - "MSBuild.UnexpectedParametersError"
helpviewer_keywords: 
  - "MSB1002"
ms.assetid: 798c9690-6d99-4f21-a491-ab44d3f3c552
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1002
**這個參數 \(Switch\) 不使用任何參數 \(Parameter\)。**  
  
 這個參數無法定義參數。  只需要參數的名稱，後面不能有冒號。  
  
### 若要更正這個錯誤  
  
-   只需要輸入這個參數的命令，不必指定參數，亦即輸入 `msbuild /<switch>`，而非 `msbuild /<switch>:<parameters>`。  
  
-   移除參數名稱後面的冒號，亦即輸入 `msbuild /<switch>`，而非 `msbuild /<switch>:`。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)