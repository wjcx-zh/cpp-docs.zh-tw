---
title: "MSBuild 錯誤 MSB3021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3021
**無法將檔案 "'\<file\>'" 複製到 "'\<file\>'"。'  \<error\>'**  
  
 `Copy` 工作無法複製指定的檔案。  
  
### 若要更正這個錯誤  
  
-   檢查目標檔案是否已由另一個應用程式鎖定 \(使用中\)。  請確認您具有讀取原始程式檔以及將目標檔案寫入目標資料夾的權限。  如果目的檔案路徑非常長，您可能需要複製到不同的位置。  
  
## 請參閱  
 [Copy Task](../Topic/Copy%20Task.md)   
 [工作](../Topic/MSBuild%20Tasks.md)