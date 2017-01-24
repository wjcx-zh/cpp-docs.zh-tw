---
title: "編譯器警告 (層級 1) C4116 | Microsoft Docs"
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
  - "C4116"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4116"
ms.assetid: 25434ef3-061e-4252-91a5-0fe2a4b2ffb3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4116
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

括號中未命名型別的定義  
  
 括號運算式中定義了不具名稱的結構、等位或列舉型別。  這個型別定義是無意義的。  
  
 在 C 函式呼叫中，此定義具有全域範圍。  在 C\+\+ 函式呼叫中，此定義和正在呼叫的函式之範圍是相同的。