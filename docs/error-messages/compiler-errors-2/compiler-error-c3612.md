---
title: "編譯器錯誤 C3612 | Microsoft Docs"
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
  - "C3612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3612"
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 密封的類別不可以為抽象類別  
  
 以 `value` \(或 [\_\_value](../../misc/value.md)\) 定義的型別都預設為密封，而類別都是抽象的，除非該類別實作其基底的所有方法。  密封的抽象類別既不可為基底類別，也不可被具現化。  
  
 如需詳細資訊，請參閱[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下列範例會產生 C3612：  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```