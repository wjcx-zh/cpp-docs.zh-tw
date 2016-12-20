---
title: "編譯器錯誤 C3207 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3207"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3207"
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3207
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 'arg' 的無效樣板引數，必須是類別樣板  
  
 樣板函式定義為使用樣板類樣板引數。 不過，已傳遞樣板類型引數。  
  
 下列範例會產生 C3207：  
  
```  
// C3207.cpp template <template <class T> class TT> void f(){} template <class T> struct S { }; void f1() { f<S<int> >();   // C3207 // try the following line instead // f<S>(); }  
```