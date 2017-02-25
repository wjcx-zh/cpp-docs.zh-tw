---
title: "編譯器警告 (層級 4) C4062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4062"
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 4) C4062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在列舉 'enumeration' 的 switch 中未處理列舉程式 'identifier'  
  
 列舉在 `switch` 陳述式中不具相關聯的處理常式，且沒有任何**預設**標籤。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4062：  
  
```  
// C4062.cpp // compile with: /W4 #pragma warning(default : 4062) enum E { a, b, c }; void func ( E e ) { switch(e) { case a: case b: break;   // no default label }   // C4062, enumerate 'c' not handled } int main() { }  
```