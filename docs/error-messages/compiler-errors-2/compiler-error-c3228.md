---
title: "編譯器錯誤 C3228 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3228"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3228"
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3228
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 'param' 的泛型類型引數不可為 'type'，它必須是實值類型或控制代碼類型  
  
 傳遞了不正確的類型作為泛型類型引數。  
  
 下列範例會產生 C3228：  
  
```  
// C3228.cpp // compile with: /clr class A {}; value class B {}; generic <class T> void Test() {} ref class C { public: generic <class T> static void f() {} }; int main() { C::f<A>();   // C3228 C::f<B>();   // OK Test<C>();   // C3228 Test<C ^>();   // OK }  
```