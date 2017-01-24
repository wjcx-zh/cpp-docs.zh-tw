---
title: "MSBuild 錯誤 MSB3152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3152
**MSB3152: 必要條件的安裝位置沒有設定為「元件廠商的網站」，且磁碟上找不到項目 '\<package\>' 中的檔案 '\<file\>'。  如需詳細資訊，請參閱 \[說明\]。**  
  
 當必要安裝程式所需要的檔案遺失時，就會發生這個錯誤。  安裝程式檔案是放在 Visual Studio 保留給可轉散發套件的特殊資料夾中。  這個資料夾會依用於開發的 Visual Studio 版本而有所不同。  如需特定資料夾位置的詳細資訊，請參閱[建立啟動載入器套件](../Topic/Creating%20Bootstrapper%20Packages.md)。  
  
### 若要更正這個錯誤  
  
-   檢查磁碟上是否存在此檔案。  
  
-   使用 HomeSite 嘗試解決套件的問題。  
  
-   將專案檔中的 `CopyComponents` 設為 `false`。  
  
-   不要使用損壞的啟動載入器套件。  
  
## 請參閱  
 [建立啟動載入器套件](../Topic/Creating%20Bootstrapper%20Packages.md)