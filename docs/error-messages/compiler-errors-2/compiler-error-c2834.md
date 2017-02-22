---
title: "編譯器錯誤 C2834 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2834"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2834"
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2834
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operator' 必須全域限定  
  
 `new` 和 `delete` 運算子會繫結至所在的類別。  範圍解析不能用來從其他類別選取其他版本的 `new` 或 `delete`。  若要實作多種型式的 `new` 或 `delete` 運算子，請使用額外的型式參數，建立其他版本的運算子。