---
title: "編譯器錯誤 C3697 | Microsoft Docs"
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
  - "C3697"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3697"
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3697
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'qualifier' : 不能在 '^' 上使用這個限定詞  
  
 追蹤處理已套用至未經設計的限定詞。  
  
 下列範例會產生 C3697：  
  
```  
// C3697.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String ^__restrict s;   // C3697  
   String ^ s2;   // OK  
}  
```