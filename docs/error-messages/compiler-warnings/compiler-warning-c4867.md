---
title: "編譯器警告 C4867 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4867"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4867"
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 編譯器警告 C4867
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 函式呼叫遺漏引數清單，請用 'call' 建立成員的指標  
  
 成員函式的指標未正確進行初始化。  
  
 對 Visual C\+\+ 2005 的編譯器完成一致性處理後可能會產生這項警告：增強型成員指標一致性。在 Visual C\+\+ 2005 以前編譯的程式碼現在會產生 C4867。  
  
 這項警告一律都以錯誤發出。  請使用 [warning](../../preprocessor/warning.md) Pragma，停用這項警告。  如需有關 C4867 和 MFC\/ATL 的詳細資訊，請參閱 [\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)。  
  
## 範例  
 下列範例會產生 C4867。  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```