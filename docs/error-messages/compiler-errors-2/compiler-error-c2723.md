---
title: "編譯器錯誤 C2723 | Microsoft Docs"
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
  - "C2723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2723"
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 函式定義上的 'specifier' 規範不合法  
  
 規範不能出現在類別宣告之外的函式定義。  只可以在類別宣告中的成員函式宣告上指定 `virtual` 規範。  
  
 下列範例會產生 C2723，並示範如何修正此問題：  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```