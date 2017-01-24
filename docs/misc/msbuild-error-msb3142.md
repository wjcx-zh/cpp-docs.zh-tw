---
title: "MSBuild 錯誤 MSB3142 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3142
**MSB3142: 嘗試將 '\<file\>' 複製到 '\<folder\>' 時發生錯誤: '\<error\>'**  
  
 將 setup.bin 複製到建置輸出目錄時，可能會產生這個錯誤訊息。  發生這個錯誤訊息的可能原因如下：  
  
-   您不具有將檔案複製到輸出目錄的權限。  
  
-   磁碟已滿。  
  
 這些都是造成 file.copy 或 directory.createdirectory 失敗的可能原因。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)