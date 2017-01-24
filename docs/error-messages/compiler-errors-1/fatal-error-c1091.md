---
title: "嚴重錯誤 C1091 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1091"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1091"
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1091
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：字串長度超過 'length' 個位元組的上限  
  
 字串常數超過目前的字串長度限制。  
  
 您可能想要將靜態字串分割成兩個 \(含\) 以上的變數，並使用 [strcpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 將結果聯結作為宣告的一部分或在執行階段時聯結。