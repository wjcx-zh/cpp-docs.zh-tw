---
title: "編譯器錯誤 C3222 | Microsoft Docs"
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
  - "C3222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3222"
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter'：無法對 Managed 或 WinRT 類型或泛型函式的成員函式宣告預設引數  
  
 不允許宣告具有預設引數的方法參數。  方法的多載形式是解決這個問題的一種方法。  也就是說，定義不含參數的同名方法，然後在方法主體中初始化變數。  
  
 下列範例會產生 C3222：  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
  
 下列範例會產生 C3222：  
  
```  
// C3222.cpp  
// compile with: /clr:oldSyntax  
public __gc class G {  
   void f( int n = 0 );   // C3222  
};  
```