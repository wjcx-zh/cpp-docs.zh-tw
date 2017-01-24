---
title: "MSBuild 錯誤 MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3165
**MSB3165: '\<public key\>' 屬性在 '\<package\>' 中的值，與檔案 '\<file\>' 中的值不相符。**  
  
 如果啟動載入器 \(Bootstrapper\) 封裝檔案中所指定的公開金鑰與磁碟上可轉散發套件的簽章不相符，或者可轉散發套件尚未簽署，就會出現這個警告訊息。  如果已簽署，組建會採用磁碟上的公開金鑰值；如果未簽署，則會採用磁碟上可轉散發套件的雜湊。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)   
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)