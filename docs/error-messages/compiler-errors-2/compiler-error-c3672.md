---
title: "編譯器錯誤 C3672 | Microsoft Docs"
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
  - "C3672"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3672"
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3672
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

虛擬解構函式運算式只能做為函式呼叫的一部分  
  
 解構函式未正確地呼叫。如需詳細資訊，請參閱[解構函式](../../cpp/destructors-cpp.md)。  
  
## 範例  
 下列範例會產生 C3672。  
  
```  
// C3672.cpp  
template<typename T>  
void f(T* pT) {  
   &pT->T::~T;   // C3672  
   pT->T::~T();   // OK  
};  
  
int main() {  
   int i;  
   f(&i);  
}  
```