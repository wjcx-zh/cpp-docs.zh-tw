---
title: "編譯器錯誤 C2692 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2692"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2692"
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器錯誤 C2692
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function\_name' : 使用 '\/clr' 選項的 C 編譯器中必須有完全原型函式  
  
 當對 .NET Managed 程式碼進行編譯時，C 編譯器需要 ANSI 函式宣告。  除此之外，如果函式未使用參數，則它必須明確宣告參數型別為 `void`。