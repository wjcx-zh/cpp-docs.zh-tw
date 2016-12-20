---
title: "編譯器錯誤 C3268 | Microsoft Docs"
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
  - "C3268"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3268"
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3268
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 泛型類別的泛型函式或成員函式不能有變數參數清單  
  
 如需詳細資訊，請參閱 [Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3268。  
  
```  
// C3268.cpp // compile with: /clr:pure /c generic <class ItemType> void Test(ItemType item, ...) {}   // C3268 // try the following line instead // void Test(ItemType item) {} generic <class ItemType2> ref struct MyStruct { void Test(...){} };   // C3268 // try the following line instead // ref struct MyStruct { void Test2(){} };   // OK  
```