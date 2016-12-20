---
title: "編譯器錯誤 C3063 | Microsoft Docs"
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
  - "C3063"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3063"
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3063
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算子 'operator' : 所有運算元必須具有相同的列舉型別  
  
 在列舉值上使用運算子時，兩個運算元都必須是該列舉型別。  如需詳細資訊，請參閱[使用運算子和列舉型別](../../misc/operators-and-enumerations.md)。  
  
 下列範例會產生 C3063：  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```