---
title: "沒有原型的函式 | Microsoft Docs"
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
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 沒有原型的函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於沒有完整原型的函式，呼叫端將會傳遞整數值做為整數，並傳遞浮點值做為雙精度值。  \(僅限浮點值\) 整數暫存器和浮點暫存器將會包含 float 值，以防被呼叫端需要整數暫存器中的值。  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)