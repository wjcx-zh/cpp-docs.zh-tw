---
title: "編譯器警告 C4694 | Microsoft Docs"
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
  - "C4694"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4694"
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4694
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class\_1': 密封抽象類別不能有基底類別 'base\_class'  
  
 抽象和密封類別無法從參考類型繼承，密封和抽象類別無法實作基底類別函式，也不允許自己用作為基底類別。  
  
 如需詳細資訊，請參閱[abstract](../../windows/abstract-cpp-component-extensions.md)、[sealed](../../windows/sealed-cpp-component-extensions.md)和[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4694。  
  
```  
// C4694.cpp // compile with: /c /clr ref struct A {}; ref struct B sealed abstract : A {};   // C4694  
```