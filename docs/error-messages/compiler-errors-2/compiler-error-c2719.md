---
title: "編譯器錯誤 C2719 | Microsoft Docs"
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
  - "C2719"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2719"
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2719
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter'：具有 \_\_declspec\(align\('\#'\)\) 的型式參數不會對齊  
  
 不允許在函式參數上使用 [align](../../cpp/align-cpp.md) `__declspec` 修飾詞。  函式參數對齊可藉由呼叫使用的慣例來控制。  如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。  
  
 下列範例會產生 C2719，並說明如何加以修正：  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```