---
title: "編譯器警告 (層級 4) C4516 | Microsoft Docs"
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
  - "C4516"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4516"
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4516
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::symbol' : 不鼓勵使用存取宣告; 建議使用成員 using 宣告代替  
  
 The ANSI C\+\+ 委員會聲明存取宣告 \(未用 [using](../../cpp/using-declaration.md) 關鍵字而更改衍生類別中成員的存取\) 已過期。  未來的 C\+\+ 版本可能不支援存取宣告。  
  
 下列範例會產生 C4516：  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```