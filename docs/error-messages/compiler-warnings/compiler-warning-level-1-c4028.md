---
title: "編譯器警告 (層級 1) C4028 | Microsoft Docs"
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
  - "C4028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4028"
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型式參數 'number' 與來自宣告的不同  
  
 型式參數的型別與宣告中相對應的參數不符合。  會使用原始宣告中的型別。  
  
 這種警告僅會出現在 C 原始程式碼。  
  
## 範例  
 下列範例會產生 C4028。  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```