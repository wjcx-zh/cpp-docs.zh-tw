---
title: "編譯器警告 (層級 3) C4608 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4608"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4608"
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 3) C4608
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'union\_member' 已由初始設定式清單中的等位成員 'union\_member' 初始化  
  
 初始化清單中相同等位的兩個成員已初始化。  您只能存取等位的一個成員。  
  
 下列範例會產生 C4608：  
  
```  
// C4608.cpp  
// compile with: /W3 /c  
class X {  
public:  
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608  
   // try the following line instead  
   // X(char c) : m_c(c) {}  
  
private:  
   union {  
      int m_i;  
      char m_c;  
   };  
};  
  
union Y {  
public:  
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608  
  
private:  
   double m_number;  
   char * m_string;  
};  
```