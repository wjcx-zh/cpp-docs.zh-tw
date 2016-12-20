---
title: "編譯器錯誤 C3208 | Microsoft Docs"
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
  - "C3208"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3208"
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3208
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 類別樣板 'class' 的樣板參數清單不符合樣板類樣板參數 'parameter' 的樣板參數清單  
  
 樣板類樣板參數沒有與所提供類別樣板相同的樣板參數數目。  
  
 下列範例會產生 C3208：  
  
```  
// C3208.cpp template <template <class T> class TT > int f(); template <class T1, class T2> struct S; template <class T1> struct R; int i = f<S>();   // C3208 // try the following line instead // int i = f<R>();  
```