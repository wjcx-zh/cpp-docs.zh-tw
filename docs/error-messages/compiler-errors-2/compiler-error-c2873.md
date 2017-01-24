---
title: "編譯器錯誤 C2873 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2873"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2873"
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2873
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 不可以在 using 宣告中使用符號  
  
 `using` 指示詞遺漏了 [namespace](../../misc/namespace-declaration.md) 關鍵字。  這使得編譯器將程式碼錯誤解譯為 [using 宣告](../../cpp/using-declaration.md)而非 [using 指示詞](../../misc/using-directive-cpp.md)。