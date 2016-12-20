---
title: "編譯器錯誤 C2675 | Microsoft Docs"
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
  - "C2675"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2675"
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2675
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一元運算子 'operator' : 'type' 沒有定義此運算子或預先定義運算子可接受的型別轉換  
  
 使用一元運算子時，而型別未定義運算子或預先定義可接受的型別轉換，也可能會發生 C2675。  若要使用此運算子，您必須將此運算子對指定的型別加以多載，或定義一個此運算子已定義型別的轉換。  
  
## 範例  
 下列範例會產生 C2675。  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```