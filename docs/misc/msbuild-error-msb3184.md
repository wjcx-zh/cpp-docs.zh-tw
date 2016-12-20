---
title: "MSBuild 錯誤 MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3184
**MSB3184: 輸入資訊清單無效。**  
  
 當建置處理序試圖載入檔案，以為它會包含應用程式資訊清單或部署資訊清單，而結果並沒有包含預期的資訊清單 \(例如所包含的是其他的資訊清單，或者包含的資料毀損\)，此時就會產生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   請檢查專案中的資訊清單是否有效而適當。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)