---
title: "MSBuild 錯誤 MSB3124 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3124
**MSB3124: 已經對副檔名 '\<extensionname\>' 建立過檔案關聯。**  
  
 在遇到重複的檔案關聯副檔名時，就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
-   移除不是唯一的 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md) `extension` 屬性 \(Attribute\)。  列出的每個 \<fileAssociation\> 項目的副檔名屬性都必須是唯一的。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)