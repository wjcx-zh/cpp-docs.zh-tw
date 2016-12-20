---
title: "編譯器警告 (層級 1) C4090 | Microsoft Docs"
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
  - "C4090"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4090"
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4090
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation' : 不同的 'modifier' 限定詞  
  
 運算中的變數是使用指定的修飾詞來定義的，此修飾詞用以防止變數未經編譯器察覺而被修改。  此運算式未經修改進行編譯。  
  
 當 **const** 或 `volatile` 項目的指標指派給未宣告為指向 **const** 或 `volatile` 的指標時，可能就會引發這項警告。  
  
 C 程式發出這項警告。  在 C\+\+ 程式中，編譯器發出錯誤：[C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)。  
  
 下列範例會產生 C4090：  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```