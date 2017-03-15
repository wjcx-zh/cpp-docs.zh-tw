---
title: "編譯器錯誤 C2679 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2679"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2679"
ms.assetid: 1a5f9d00-9190-4aa6-bc72-949f68ec136f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2679
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

二元運算子 'operator' : 找不到使用右方運算元型別 'type' 的運算子 \(或是沒有可接受的轉換\)  
  
 若要使用此運算子，您必須將此運算子對指定的型別加以多載，或定義一個此運算子已定義型別的轉換。  
  
 下列範例會產生 C2679：  
  
```  
// C2679.cpp  
class C {  
public:  
   C();   // no constructor with an int argument  
} c;  
  
class D {  
public:  
   D(int) {}  
   D(){}  
} d;  
  
int main() {  
   c = 10;   // C2679  
   d = 10;   // OK  
}  
```