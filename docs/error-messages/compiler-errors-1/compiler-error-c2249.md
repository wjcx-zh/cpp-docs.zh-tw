---
title: "編譯器錯誤 C2249 | Microsoft Docs"
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
  - "C2249"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2249"
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2249
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 沒有可存取的路徑以存取宣告在虛擬基底 'class' 中的成員  
  
 `member` 是繼承自非公用的 `virtual` 基底類別或結構。  
  
## 範例  
 下列範例會產生 C2249。  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## 範例  
 如果您嘗試從 Standard C\+\+ 程式庫指定資料流至另一個資料流，也會發生 C2249。下列範例會產生 C2249。  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```