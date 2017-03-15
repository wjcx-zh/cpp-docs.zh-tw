---
title: "編譯器警告 (層級 1) C4489 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4489"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4489"
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 編譯器警告 (層級 1) C4489
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'specifier' : 不允許出現在介面方法 'method' 上，覆寫規範只允許出現在 ref 類別和實值類別方法上  
  
 不正確地在介面方法上使用規範關鍵字。  
  
 如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4489。  
  
```  
// C4489.cpp  
// compile with: /clr /c /W1  
public interface class I {   
   void f() new;   // C4489  
   virtual void b() override;   // C4489  
  
   void g();   // OK  
};  
```