---
title: "MSBuild 錯誤 MSB3146 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3146
**MSB3146: '\<package\>' 需要項目 '\<package\>'，但卻不包含。**  
  
 如果某個啟動載入器套件相依於另一個啟動載入器套件，但您只選擇安裝相依套件，就會發生這個錯誤訊息。  例如，套件 B 相依於套件 A，但只安裝了 B。  
  
### 若要更正這個錯誤  
  
-   加入所需的套件。