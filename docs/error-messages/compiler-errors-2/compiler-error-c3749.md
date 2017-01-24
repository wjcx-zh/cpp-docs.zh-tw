---
title: "編譯器錯誤 C3749 | Microsoft Docs"
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
  - "C3749"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3749"
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3749
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute' : 自訂屬性無法用於函式內  
  
 不能在函式中使用自訂屬性 \(如需關於自訂屬性的詳細資訊，請參閱主題[屬性](../../windows/attribute.md)\)。  
  
 下列範例會產生 C3749：  
  
```  
// C3749a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref struct ABC : public Attribute {  
   ABC() {}  
};  
  
void f1() { [ABC]; };  // C3749  
```  
  
 下列範例會產生 C3749：  
  
```  
// C3749b.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
  
[attribute(All)]  
public __gc struct ABC {  
   ABC() {}  
};  
  
void f1() { [ABC]; };  // C3749  
```