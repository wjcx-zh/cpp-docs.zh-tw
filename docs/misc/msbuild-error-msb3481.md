---
title: "MSBuild 錯誤 MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3481
**MSB3481: 找不到簽署憑證。  請確認該憑證位於目前使用者的個人存放區中。**  
  
 如果在個人憑證存放區中找不到簽署憑證，就會產生這個錯誤訊息。  這個錯誤訊息類似於 [MSBuild 錯誤 MSB3486](../misc/msbuild-error-msb3486.md)，這表示雖然找到憑證，但憑證不相符。  
  
### 若要更正這個錯誤  
  
-   確認個人憑證存放區中存在符合專案 .pfx 檔的有效憑證。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)