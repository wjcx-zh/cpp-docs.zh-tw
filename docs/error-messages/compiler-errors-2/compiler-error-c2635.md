---
title: "編譯器錯誤 C2635 | Microsoft Docs"
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
  - "C2635"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2635"
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2635
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法將 'identifier1\*' 轉換成 'identifier2\*'; 虛擬基底類別是隱含轉換  
  
 不允許需要從 `virtual` 基底類別轉換為衍生類別的轉換。  
  
 下列範例會產生 C2635：  
  
```  
// C2635.cpp  
class B {};  
class D : virtual public B {};  
class E : public B {};  
  
int main() {  
   B b;  
   D d;  
   E e;  
  
   D * pD = &d;  
   E * pE = &e;  
   pD = (D*)&b;   // C2635  
   pE = (E*)&b;   // OK  
}  
```