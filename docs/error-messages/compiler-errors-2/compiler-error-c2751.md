---
title: "編譯器錯誤 C2751 | Microsoft Docs"
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
  - "C2751"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2751"
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2751
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter' : 不可以限定函式參數的名稱  
  
 您不能將限定名稱 \(Qualified Name\) 用作函式參數。  
  
 下列範例會產生 C2751：  
  
```  
// C2751.cpp  
namespace std {  
   template<typename T>  
   class list {};  
}  
  
#define list std::list  
void f(int &list){}   // C2751  
```