---
title: "MSBuild 錯誤 MSB3120 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionTooLong"
helpviewer_keywords: 
  - "MSB3120"
ms.assetid: 20bc64f5-aadc-4eec-9915-a87a3d7f81ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3120
**MSB3120: 檔案關聯副檔名 '\<extension\>' 超過允許的最大長度 \<maximumlength\>。**  
  
 檔案關聯副檔名中的字元數目不可超過指定的數目。  
  
### 若要更正這個錯誤  
  
-   將 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md) `extension` 屬性 \(Attribute\) 設定成內含字元數目不超過目標作業系統容許上限的值。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)