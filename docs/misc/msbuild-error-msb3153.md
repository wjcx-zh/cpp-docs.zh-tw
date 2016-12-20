---
title: "MSBuild 錯誤 MSB3153 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageValidation"
helpviewer_keywords: 
  - "MSB3153"
ms.assetid: 937bb1ff-79f7-45a5-a085-525f4b48ea4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3153
**MSB3153: 位於 '\<folder\>' 的項目 '\<package\>' 未通過 Xml 驗證。**  
  
 如果資訊清單 \(特別是 package.xml\) 沒有通過 XML 驗證，就會產生這個警告訊息。  後續的錯誤訊息中 \([MSBuild 錯誤 MSB3159](../misc/msbuild-error-msb3159.md) 或 [MSBuild 錯誤 MSB3160](../misc/msbuild-error-msb3160.md)\) 會列出特定問題。  
  
### 若要更正這個錯誤  
  
-   解決後續的錯誤訊息中所列出的資訊清單驗證問題。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)