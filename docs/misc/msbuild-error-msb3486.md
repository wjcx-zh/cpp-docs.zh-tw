---
title: "MSBuild 錯誤 MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3486
**MSB3486: 無法從存放區 '\<certificate store\>' 取得憑證。**  
  
 如果在個人憑證存放區中找不到符合專案 .pfx 檔指模的憑證，`ResolveKeySource` MSBuild 工作就會產生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   確認專案 .pfx 檔的指模符合個人憑證存放區中憑證的指模。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)