---
title: "編譯器錯誤 C3290 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3290"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3290"
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3290
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type : trivial 屬性不能有參考類型  
  
 屬性宣告不正確。 當您宣告 trivial 屬性時，編譯器會建立屬性將更新的變數，而且類別中不可以有追蹤參考變數。  
  
 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 和 [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3290。  
  
```  
// C3290.cpp // compile with: /clr /c ref struct R {}; ref struct X { R^ mr; property R % y;   // C3290 property R ^ x;   // OK // OK property R% prop { R% get() { return *mr; } void set(R%) {} } }; int main() { X x; R% xp = x.prop; }  
```