---
title: "編譯器錯誤 C2917 | Microsoft Docs"
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
  - "C2917"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2917"
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2917
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name': 無效的樣板\-參數  
  
 樣板參數清單包含不是樣板參數的識別項。  
  
## 範例  
 下列範例會產生 C2917：  
  
```  
// C2917.cpp // compile with: /c template<class T> class Vector { void sort(); }; template<class T*> void Vector<T>::sort() {}   // C2917 // try the following line instead // template<class T> void Vector<T>::sort() {}  
```