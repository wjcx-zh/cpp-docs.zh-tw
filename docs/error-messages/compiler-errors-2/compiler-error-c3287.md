---
title: "編譯器錯誤 C3287 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3287"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3287"
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3287
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類型 'type' \(GetEnumerator 的傳回類型\) 必須有適合的公用 MoveNext 成員函式和公用 Current 屬性  
  
 使用者定義的集合類別必須包含 `MoveNext` 和 `Current` 的定義。  
  
 如需詳細資訊，請參閱 [如何：使用 for each 反覆查看使用者定義的集合](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)。  
  
## 範例  
 下列範例會產生 C3287。  
  
```  
// C3287.cpp // compile with: /clr using namespace System; ref struct R { bool MoveNext() { return true; } property Object^ Current { Object^ get() { Object ^ o = gcnew Object; return o; } } }; ref struct R2 { R ^GetEnumerator() { R^ r = gcnew R; return r; } }; ref struct T {}; ref struct T2 { T ^GetEnumerator() { T^ t = gcnew T; return t; } }; int main() { for each (int i in gcnew T2) {}   // C3287 for each (int i in gcnew R2) {}   // OK }  
```