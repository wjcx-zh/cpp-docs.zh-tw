---
title: "函式呼叫轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式呼叫, 引數類型轉換"
  - "函式呼叫, 轉換"
  - "函式 [C], 引數轉換"
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 函式呼叫轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在函式呼叫的引數上執行的類型轉換取決於函式原型 \(向前宣告\) 是否存在，以及所呼叫之函式宣告的引數類型。  
  
 如果函式原型存在並且包含宣告的引數類型，編譯器會執行類型檢查 \(請參閱[函式](../c-language/functions-c.md)\)。  
  
 如果函式原型不存在，則只會在函式呼叫中的引數上執行一般算術轉換。  這些轉換會單獨在呼叫中的各個引數上執行。  這表示 **float** 值會轉換成 **double**，`char` 或 **short** 值會轉換為 `int`，而 `unsigned char` 或 **unsigned short** 會轉換為 `unsigned int`。  
  
## 請參閱  
 [類型轉換](../c-language/type-conversions-c.md)