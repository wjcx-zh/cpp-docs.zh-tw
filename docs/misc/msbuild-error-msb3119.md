---
title: "MSBuild 錯誤 MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3119
**MSB3119：檔案關聯副檔名必須以句點字元 \(.\) 開頭。**  
  
 當您設定了檔案關聯，而副檔名開頭不是句號字元 \(.\) 時，就會發生這個錯誤。  
  
### 若要更正這個錯誤  
  
-   將 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md) `extension` 屬性設定成以句號字元 \(.\) 開頭的值，例如 ".doc"。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)