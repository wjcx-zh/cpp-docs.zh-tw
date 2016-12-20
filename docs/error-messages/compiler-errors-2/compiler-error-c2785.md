---
title: "編譯器錯誤 C2785 | Microsoft Docs"
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
  - "C2785"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2785"
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2785
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration1' 和 'declaration2' 擁有不同的傳回型別  
  
 函式樣板特製化的傳回型別和主要函式樣板的傳回型別不同。  
  
### 更正這個錯誤  
  
1.  對所有的函式樣板特製化進行一致性檢查。  
  
## 範例  
 下列範例會產生 C2785：  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```