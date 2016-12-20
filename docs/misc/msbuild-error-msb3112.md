---
title: "MSBuild 錯誤 MSB3112 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateAssemblyIdentity"
helpviewer_keywords: 
  - "MSB3112"
ms.assetid: 90f25254-8148-49ea-9a5a-213feda16df0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3112
**MSB3112: 有兩個以上的組件具有相同的識別 '\<assembly\>'。**  
  
 如果有一個以上的參考組件具有相同的識別，就會產生這個警告訊息。  
  
### 若要更正這個錯誤  
  
-   從專案中移除其中一個參考組件。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)