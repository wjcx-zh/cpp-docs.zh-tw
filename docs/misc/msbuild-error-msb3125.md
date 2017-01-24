---
title: "MSBuild 錯誤 MSB3125 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNoEntryPoint"
helpviewer_keywords: 
  - "MSB3125"
ms.assetid: f8a08b05-1946-4788-8577-ceefde785e95
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3125
**MSB3125: 此應用程式使用檔案關聯，但是沒有 EntryPoint 組建參數。**  
  
 當 entryPoint 組建 \(Build\) 參數不存在時，就會發生這個錯誤。  將應用程式設定為使用檔案關聯時，應用程式資訊清單中必須有 entryPoint 組建參數。  \<entryPoint\> 項目識別應用程式執行時應該執行的組件 \(Assembly\)。  
  
### 若要更正這個錯誤  
  
-   將 [\<entryPoint\> 項目](../Topic/%3CentryPoint%3E%20Element%20\(ClickOnce%20Application\).md) 設為有效值。  如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md)