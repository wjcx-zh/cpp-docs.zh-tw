---
title: "MSBuild 錯誤 MSB3141 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3141
**MSB3141: 在項目 '\<package\>' 中沒有指定檔案 '\<file\>' 的 'PublicKey' 或 'Hash' 屬性。**  
  
 如果您試圖針對啟動載入器套件使用 HomeSite，就會發生這個錯誤訊息。  然而，啟動載入器資訊清單並沒有包含執行階段檔案驗證 \(也沒有公開金鑰或雜湊\) 的正確資訊。  
  
### 若要更正這個錯誤  
  
-   下載遺漏資訊的套件檔，並將它複製到啟動載入器快取區中。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)