---
title: "MSBuild 錯誤 MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3143
**MSB3143: 嘗試複製項目 '\<package\>' 的 '\<file\>' 時發生錯誤: '\<error\>'**  
  
 當啟動載入器套件複製到建置輸出目錄時，可能會發生這個錯誤訊息。  發生這個錯誤訊息的可能原因如下：  
  
-   您不具有將檔案複製到建置輸出目錄的權限。  
  
-   磁碟已滿。  
  
 這些都是造成 file.copy 或 directory.createdirectory 失敗的可能原因。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)