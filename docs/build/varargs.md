---
title: "Varargs | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Varargs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果參數經由 varargs \(例如省略引數\) 傳遞，基本上會適用正常的參數傳遞，包括遺漏第五個和後續的引數。  傾印位址被取用的引數，也是被呼叫端的責任。  對於只有浮點數值的情況，整數和浮點數暫存器都會包含浮點值，以免被呼叫端在整數暫存器中尋找參數值。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)