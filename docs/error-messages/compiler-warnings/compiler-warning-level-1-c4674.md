---
title: "編譯器警告 (層級 1) C4674 | Microsoft Docs"
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
  - "C4674"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4674"
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4674
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'method' 必須宣告為 'static'，而且只能有一個參數  
  
 轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。  
  
 使用新語法 \(**\/clr**\) 時，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)和[使用者定義轉換](../../dotnet/user-defined-conversions-cpp-cli.md)，以了解運算子定義的相關資訊。  
  
## 範例  
 下列範例會產生 C4674。  
  
```  
// C4674.cpp // compile with: /clr /WX /W1 /LD ref class G { int op_Implicit(int i) {   // C4674 return 0; } };  
```  
  
## 範例  
 下列範例會產生 C4674。  
  
```  
// C4674_b.cpp // compile with: /clr:oldSyntax /W1 /LD __gc class G { int op_Implicit(int i) {   // C4674 // try the following line instead // static int op_Implicit(int i) { return 0; } };  
```