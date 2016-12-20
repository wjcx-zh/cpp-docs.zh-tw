---
title: "編譯器錯誤 C3215 | Microsoft Docs"
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
  - "C3215"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3215"
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3215
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1': 泛型類型參數已經受到 'type2' 的條件約束  
  
 條件約束指定了一次以上。  
  
 如需泛型的詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
 下列範例會產生 C3215：  
  
```  
// C3215.cpp // compile with: /clr interface struct A {}; generic <class T> where T : A,A ref class C {};   // C3215  
```  
  
 可能的解決方式：  
  
```  
// C3215b.cpp // compile with: /clr /c interface struct A {}; generic <class T> where T : A ref class C {};  
```