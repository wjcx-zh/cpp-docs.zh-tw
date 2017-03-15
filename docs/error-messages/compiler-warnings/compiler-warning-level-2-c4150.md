---
title: "編譯器警告 (層級 2) C4150 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4150"
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 2) C4150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除指向不完整型別 'type' 的指標; 沒有解構函式可呼叫  
  
 **delete** 運算子被呼叫來刪除某個已宣告但未定義的型別，所以編譯器找不到解構函式 \(Destructor\)。  
  
 下列範例會產生 C4150：  
  
```  
// C4150.cpp  
// compile with: /W2  
class  IncClass;  
  
void NoDestruct( IncClass* pIncClass )  
{  
   delete pIncClass;  
} // C4150, define class to resolve  
  
int main()  
{  
}  
```