---
title: "MSBuild 錯誤 MSB3145 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3145
**MSB3145: 建置輸入參數 '\<property\>\=\<value\>' 不是 Web URL 或 UNC 共用。**  
  
 當 `SupportUrl`、`ComponentsUrl` 或 `ApplicationUrl` 專案屬性的值無效時，就會發生這個錯誤訊息。  此值必須是有效的 URI 或 UNC 路徑。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)