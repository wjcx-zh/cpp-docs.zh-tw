---
title: "編譯器警告 (層級 4) C4510 | Microsoft Docs"
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
  - "C4510"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4510"
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4510
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : 無法產生預設的建構函式  
  
 編譯器無法產生指定類別的預設建構函式，而且沒有建立使用者定義的建構函式。  您無法建立這種型態的物件。  
  
 有幾種狀況會使編譯器無法產生預設的建構函式，包括：  
  
-   常數資料成員。  
  
-   為參考的資料成員。  
  
 您需要為初始化這些成員的類別建立一個使用者定義的預設建構函式。  
  
 下列範例會產生 C4510：  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```