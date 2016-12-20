---
title: "MSBuild 錯誤 MSB1024 | Microsoft Docs"
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
  - "MSBuild.MultipleSchemasError"
helpviewer_keywords: 
  - "MSB1024"
ms.assetid: dff30870-da1a-479f-998b-03d0f5e16088
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1024
**專案的驗證只能指定一個結構描述。**  
  
 **\/validate** 參數只能指定一個結構描述。  
  
### 若要更正這個錯誤  
  
1.  驗證專案時只能使用 `/validate:<schema>` 格式指定一個結構描述，例如 `/validate:MyExtendedBuildSchema.xsd`。  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)