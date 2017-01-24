---
title: "MSBuild 錯誤 MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3164
**MSB3164: 未提供 '\<package\>' 的 'HomeSite' 屬性，因此套件將與啟動載入器發行到相同的位置。**  
  
 當使用者想要使用 HomeSite，但指定套件卻沒有適當的 HomeSite 資訊可用，此時就會產生這個警告訊息。  
  
### 若要更正這個錯誤  
  
-   更新資訊清單檔案以加入 HomeSite 資訊。  
  
-   或者，不要使用 HomeSite。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)