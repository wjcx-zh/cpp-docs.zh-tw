---
title: "編譯器錯誤 C2708 | Microsoft Docs"
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
  - "C2708"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2708"
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2708
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 實質參數長度 \(以位元組為單位\) 和先前的呼叫或參考不同  
  
 [\_\_stdcall](../../cpp/stdcall.md) 函式必須有原型 \(Prototype\)。  否則，編譯器會將第一個函式呼叫解譯成原型，並且當編譯器遇到不相符的呼叫時，會出現這項錯誤。  
  
 若要修正這項錯誤，請加入一個函式原型。