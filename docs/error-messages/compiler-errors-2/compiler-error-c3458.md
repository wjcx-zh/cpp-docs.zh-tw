---
title: "編譯器錯誤 C3458 | Microsoft Docs"
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
  - "C3458"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3458"
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3458
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute1': 屬性 'attribute2 ' 已對 'construct' 指定，而這兩個屬性互斥  
  
 針對相同的建構指定了兩個互斥的屬性。  
  
## 範例  
 下列範例會產生 C3458  
  
```  
// C3458.cpp // compile with: /clr /c [System::Reflection::DefaultMember("Chars")] public ref class MyString { public: [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458 property char default[int] { char get(int index); void set(int index, char c); } };  
```