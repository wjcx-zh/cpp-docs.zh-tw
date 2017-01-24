---
title: "MSBuild 錯誤 MSB3113 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3113
**MSB3113: 找不到檔案 '\<file\>'。**  
  
 如果在建立新的資訊清單時遇到了無法解析的參考，就會產生這個錯誤訊息。  它可能是源自於專案檔或做為工作參數。  
  
### 若要更正這個錯誤  
  
-   檢查專案檔 \(以及建置參數，如果您是自訂建置\) 是否有檔案參考衝突。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)