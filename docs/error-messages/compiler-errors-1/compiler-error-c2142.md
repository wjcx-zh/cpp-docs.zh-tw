---
title: "編譯器錯誤 C2142 | Microsoft Docs"
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
  - "C2142"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2142"
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2142
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式宣告不同，只能在其中之一指定可變個數參數  
  
 函式的宣告之一包含可變個數參數清單。  另一個宣告則沒有。  僅發生於 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\)。  
  
 下列範例會產生 C2142：  
  
```  
// C2142.c  
// compile with: /Za /c  
void func();  
void func( int, ... );   // C2142  
void func2( int, ... );   // OK  
```