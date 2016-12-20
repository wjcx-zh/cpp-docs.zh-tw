---
title: "編譯器錯誤 C3296 | Microsoft Docs"
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
  - "C3296"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3296"
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3296
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'property': 已經有這個名稱的屬性  
  
 編譯器遇到具有相同名稱的多個屬性。 類型中的每個屬性都必須具有唯一的名稱。  
  
 如需詳細資訊，請參閱[property](../../windows/property-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3296。  
  
```  
// C3296.cpp // compile with: /clr /c using namespace System; ref class R { public: property int MyProp[int] { int get(int); } property String^ MyProp[int] { void set(int, String^); }   // C3296 };  
```