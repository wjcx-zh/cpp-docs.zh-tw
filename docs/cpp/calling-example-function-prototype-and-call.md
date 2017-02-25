---
title: "呼叫範例：函式原型和呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "呼叫慣例, 範例 [C++]"
  - "範例 [C++], 呼叫慣例"
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 呼叫範例：函式原型和呼叫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 下列範例示範使用各種呼叫慣例執行函式呼叫的結果。  
  
 這個範例是以下列函式架構為基礎。  以適當的呼叫慣例取代 `calltype`。  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 如需詳細資訊，請參閱[呼叫結果範例](../cpp/results-of-calling-example.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)