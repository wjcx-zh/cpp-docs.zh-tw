---
title: "MSBuild 錯誤 MSB3175 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidItemValue"
helpviewer_keywords: 
  - "MSB3175"
ms.assetid: c157e934-e4e6-43d9-abdf-cb4fb03be494
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3175
**MSB3175: 項目 '\<build task\>' 的 '\<file\>' 值無效。**  
  
 如果建置處理序無法辨識各種列舉型別架構工作項目屬性的值，例如 `AssemblyType`、`DependencyType`、`FileType` 或 `TargetZone` 的值，就會產生這個警告訊息。  應用程式資訊清單和部署資訊清單都可能會產生這個警告訊息。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)