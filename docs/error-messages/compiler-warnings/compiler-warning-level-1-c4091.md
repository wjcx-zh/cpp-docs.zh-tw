---
title: "編譯器警告 (層級 1) C4091 | Microsoft Docs"
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
  - "C4091"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4091"
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4091
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword' : 當沒有宣告變數時，忽略 'type' 的左方  
  
 編譯器偵測到以下情況：使用者可能想要讓變數進行宣告，但是編譯器無法宣告該變數。  
  
## 範例  
 位於使用者定義型別開頭的 `__declspec` 屬性套用至該型別的變數。  警告 C4091 表示未宣告任何變數。  下列範例會產生 C4091。  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## 範例  
 如果識別項是 typedef，它也無法做為變數名稱。  下列範例會產生 C4091。  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```