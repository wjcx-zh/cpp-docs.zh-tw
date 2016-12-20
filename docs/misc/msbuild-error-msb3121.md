---
title: "MSBuild 錯誤 MSB3121 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationMissingAttribute"
helpviewer_keywords: 
  - "MSB3121"
ms.assetid: c1e83a2a-515f-412d-b8b7-4821e510a923
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3121
**MSB3121: 應用程式資訊清單中的檔案關聯項目遺漏了下列其中一個或多個必要屬性: 副檔名、描述、PROGID 或預設圖示。**  
  
 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md) 必須包含所有 \(共四個\) 屬性 \(Attribute\) 的值。  
  
### 若要更正這個錯誤  
  
-   將每個 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md) 屬性都設為有效值。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)