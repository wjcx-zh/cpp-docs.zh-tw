---
title: "MSBuild 錯誤 MSB1012 | Microsoft Docs"
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
  - "MSBuild.MissingResponseFileError"
helpviewer_keywords: 
  - "MSB1012"
ms.assetid: 6e09e21d-9f64-4a8c-adec-f8efb28b7ac2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1012
**指定回應檔。**  
  
 您必須指定 @ 參數的回應檔 \(Response File\)。  
  
### 若要更正這個錯誤  
  
-   指定回應檔。  語法為 @\<file name\>，例如 `@BuildHW.txt`  
  
-   請勿在命令列中包含 @ 參數。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)