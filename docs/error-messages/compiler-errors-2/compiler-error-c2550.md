---
title: "編譯器錯誤 C2550 | Microsoft Docs"
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
  - "C2550"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2550"
ms.assetid: 3293f53e-ee66-4035-920d-34e115c3a24c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2550
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 建構函式初始設定式清單只允許在建構函式定義上  
  
 基底類別初始設定式清單用於定義非建構函式的函式。  
  
 下列範例會產生 C2550：  
  
```  
// C2550.cpp  
// compile with: /c  
class C {  
public:  
   C();  
};  
  
class D : public C {  
public:  
   D();  
   void func();  
};  
  
void D::func() : C() {}  // C2550  
D::D() : C() {}   // OK  
```