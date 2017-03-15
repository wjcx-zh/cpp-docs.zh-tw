---
title: "編譯器錯誤 C2234 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2234"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2234"
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2234
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name' : 參考的陣列不合法  
  
 因為不允許使用參考的指標，因此不可能有參考的陣列。  
  
 下列範例會產生 C2234：  
  
```  
// C2234.cpp  
int main() {  
   int i = 0, j = 0, k = 0, l = 0;  
   int &array[4] = {i,j,k,l};   // C2234  
   int array2[4] = {i,j,k,l};   // OK  
}  
```