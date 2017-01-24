---
title: "編譯器錯誤 CS2021 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS2021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2021"
ms.assetid: 8379d77e-6586-4e43-9aab-7cdf3ffecf51
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2021
檔名 'file' 太長或無效  
  
 所有傳遞至 C\# 編譯器的檔案名稱長度不得超過 `_MAX_PATH` \(定義於 Windows 標頭檔\)。 在下列情況下，編譯器將顯示這個錯誤：  
  
-   檔案名稱 \(包括路徑\) 長度超過 `_MAX_PATH`。  
  
-   檔案名稱包含無效的字元。  
  
-   不允許萬用字元的檔案名稱 \(例如資源檔名稱\) 包含萬用字元。