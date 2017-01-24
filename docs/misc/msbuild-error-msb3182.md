---
title: "MSBuild 錯誤 MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3182
**MSB3182: 檔案名稱 '\<file\>' 超過 '\<length\>' 個字元。**  
  
 當 `TargetPath` 屬性的值太長時，就會產生這個警告訊息。  應用程式和部署資訊清單都可能會發生這個警告訊息。  
  
### 若要更正這個錯誤  
  
-   編輯 `TargetPath` 屬性的值，讓它變短一點。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)