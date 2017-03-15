---
title: "編譯器錯誤 C2129 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2129"
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已經宣告靜態函式 'function'，但尚未定義  
  
 對從未定義的 `static` 函式進行向前參考 \(Forward Reference\)。  
  
 `static` 函式必須定義於檔案範圍 \(File Scope\) 內。  如果函式定義於另一個檔案中，則必須宣告成 `extern`。