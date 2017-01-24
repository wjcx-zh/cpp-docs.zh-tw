---
title: "編譯器錯誤 C2594 | Microsoft Docs"
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
  - "C2594"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2594"
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2594
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 從 'type1' 至 'type2' 的轉換模稜兩可  
  
 沒有比從 *type1* 至 *type2* 的轉換有其他任何更直接的轉換。  建議您可以使用兩種可能的解決方式來從 *type1* 轉換至 *type2*。  第一個選項是定義從 *type1* 至 *type2* 的直接轉換，第二個選項則是指定從 *type1* 至 *type2* 的轉換序列。  
  
 下列範例會產生 C2594。  此錯誤的建議解決方式是使用轉換序列：  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```