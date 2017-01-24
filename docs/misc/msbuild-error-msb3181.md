---
title: "MSBuild 錯誤 MSB3181 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3181
**MSB3181: 兩個或兩個以上的檔案具有相同的目標路徑 '\<path\>'。**  
  
 如果兩個或兩個以上的參考組件或檔案共用相同的目標路徑，就會在應用程式資訊清單產生期間產生這個警告訊息。  路徑包含了檔案名稱，所有這些組件會在部署階段彼此互相覆寫。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)