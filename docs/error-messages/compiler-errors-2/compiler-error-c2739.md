---
title: "編譯器錯誤 C2739 | Microsoft Docs"
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
  - "C2739"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2739"
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2739
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'number'：明確的 Managed 或 WinRT 陣列維度必須是介於 1 到 32 之間  
  
 陣列維度不是介於 1 到 32 之間。  
  
 下列範例會產生 C2739，並示範如何修正此問題：  
  
```  
// C2739.cpp  
// compile with: /clr  
int main() {  
   array<int, -1>^a;   // C2739  
   // try the following line instead  
   // array<int, 2>^a;  
}  
```