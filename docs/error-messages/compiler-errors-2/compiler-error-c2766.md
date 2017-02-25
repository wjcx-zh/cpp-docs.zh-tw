---
title: "編譯器錯誤 C2766 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2766"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2766"
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2766
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

明確特製化; 'specialization' 已經定義  
  
 不允許重複明確特製化。  如需詳細資訊，請參閱[函式樣板的明確特製化](../../cpp/explicit-specialization-of-function-templates.md)。  
  
 下列範例會產生 C2766：  
  
```  
// C2766.cpp  
// compile with: /c  
template<class T>   
struct A {};  
  
template<>   
struct A<int> {};  
  
template<>   
struct A<int> {};   // C2766  
// try the following line instead  
// struct A<char> {};  
```