---
title: "編譯器錯誤 C2677 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2677"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2677"
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2677
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

二元運算子 'operator' : 找不到使用型別 'type' 的全域運算子 \(或是沒有可接受的轉換\)  
  
 若要使用此運算子，您必須將此運算子對指定的型別加以多載，或定義一個此運算子已定義型別的轉換。  
  
 下列範例會產生 C2677：  
  
```  
// C2677.cpp  
class C {  
public:  
   C(){}  
} c;  
  
class D {  
public:  
   D(){}  
   operator int(){return 0;}  
} d;  
  
int main() {  
   int i = 1 >> c;   // C2677  
   int j = 1 >> d;   // OK operator int() defined  
}  
```