---
title: "編譯器錯誤 C2765 | Microsoft Docs"
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
  - "C2765"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2765"
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2765
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 函式樣板的明確特製化不能具有任何預設引數  
  
 函式様板的明確特製化上不允許有預設引數。  如需詳細資訊，請參閱[函式樣板的明確特製化](../../cpp/explicit-specialization-of-function-templates.md)。  
  
 下列範例會產生 C2765：  
  
```  
// C2765.cpp  
template<class T> void f(T t) {};  
  
template<> void f<char>(char c = 'a') {}   // C2765  
// try the following line instead  
// template<> void f<char>(char c) {}  
```