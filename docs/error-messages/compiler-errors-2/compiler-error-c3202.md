---
title: "編譯器錯誤 C3202 | Microsoft Docs"
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
  - "C3202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3202"
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg name': 樣板參數 'parameter' 的預設引數無效; 必須是類別樣板  
  
 您已傳遞樣板參數的無效預設引數。  
  
 下列範例會產生 C3202：  
  
```  
// C3202.cpp template<typename T> class X { }; class Z { }; template<template<typename U> class T1 = Z, typename T2> // C3202 class Y { };  
```