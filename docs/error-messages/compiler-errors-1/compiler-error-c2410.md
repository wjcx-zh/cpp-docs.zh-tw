---
title: "編譯器錯誤 C2410 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2410"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2410"
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C2410
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 'context' 中的成員名稱模稜兩可  
  
 識別項在此內容中為多個結構或等位 \(Union\) 的成員。  
  
 在運算元上使用結構或等位規範將導致錯誤。  結構或等位規範是 `struct` 或 `union` 型別的識別項 \(與參考的結構或等位型別相同的 `typedef` 名稱或變數\)。  規範必須是第一個成員選取運算子 \(.\) 的左運算元才能使用該運算元。