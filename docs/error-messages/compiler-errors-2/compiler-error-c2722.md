---
title: "編譯器錯誤 C2722 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2722"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2722"
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2722
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'::operator': 下列運算子命令不合法; 請使用 'operator operator'  
  
 `operator` 陳述式重複定義 `::new` 或 `::delete`。  `new` 和 `delete` 運算子都是全域，所以範圍解析 \(Scope Resolution\) 運算子 \(`::`\) 是沒有意義的。  請移除 `::` 運算子。