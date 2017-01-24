---
title: "編譯器錯誤 C2944 | Microsoft Docs"
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
  - "C2944"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2944"
ms.assetid: f209e668-e72f-442a-a438-8c4ff43a404a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2944
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class' : type\-class\-id 重複定義為樣板的數值引數  
  
 您無法使用泛型或樣板類別取代符號作為樣板數值引數。  
  
 下列範例會產生 C2944：  
  
```  
// C2944.cpp // compile with: /c template<class T> class TC { }; template <int TC<int> > struct X1 { };   // C2944 template <class T > struct X2 {};  
```  
  
 使用泛型時，也會發生 C2944：  
  
```  
// C2944b.cpp // compile with: /clr /c generic<class T> ref class GC {}; template <int GC<int> > struct X2 { };   // C2944 template <class T> struct X3 {};   // OK  
```