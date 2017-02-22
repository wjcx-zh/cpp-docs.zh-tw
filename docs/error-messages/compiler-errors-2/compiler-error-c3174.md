---
title: "編譯器錯誤 C3174 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3174"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3174"
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3174
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未指定模組屬性  
  
 使用 Visual C\+\+ 屬性的程式沒有同時使用 [module](../../windows/module-cpp.md) 屬性，該屬性在所有使用屬性的程式中都是必要項目。  
  
 下列範例會產生 C3174：  
  
```  
// C3174.cpp  
// C3174 expected  
// uncomment the following line to resolve this C3174  
// [module(name="x")];  
[export]  
struct S  
{  
   int i;  
};  
  
int main()  
{  
}  
```