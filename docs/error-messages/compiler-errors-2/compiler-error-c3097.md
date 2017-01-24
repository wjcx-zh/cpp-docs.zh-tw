---
title: "編譯器錯誤 C3097 | Microsoft Docs"
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
  - "C3097"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3097"
ms.assetid: b24bd8f8-e04f-4fbb-be57-4feb9165572e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3097
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': 屬性必須以 'assembly:' 或 'module:' 設定範圍  
  
 不正確地使用了全域屬性。  
  
 如需詳細資訊，請參閱[User\-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3097。  
  
```  
// C3097.cpp // compile with: /clr /c using namespace System; [AttributeUsage(AttributeTargets::All, AllowMultiple = true)] public ref class Attr : public Attribute { public: Attr(int t) : m_t(t) {} int m_t; }; [Attr(10)];   // C3097 [assembly:Attr(10)];   // OK [Attr(10)]   // OK public ref class MyClass {};  
```