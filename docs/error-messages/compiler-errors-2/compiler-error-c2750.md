---
title: "編譯器錯誤 C2750 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2750"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2750"
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2750
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 無法在參考型別上使用 'new'，請用 'gcnew' 代替  
  
 若要建立 CLR 型別的執行個體 \(它會讓執行個體放置於記憶體回收堆積上\)，就必須使用 [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
 下列範例會產生 C2750：  
  
```  
// C2750.cpp  
// compile with: /clr  
ref struct Y1 {};  
  
int main() {  
   Y1 ^ x = new Y1;   // C2750  
  
   // try the following line instead  
   Y1 ^ x2 = gcnew Y1;  
}  
```