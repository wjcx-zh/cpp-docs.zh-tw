---
title: "編譯器錯誤 C3390 | Microsoft Docs"
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
  - "C3390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3390"
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type\_arg' : 對泛型參數 'param' \(屬於泛型 'generic\_type'\) 無效的類型引數，必須是參考類型  
  
 泛型類型未正確地具現化。  請檢查類型定義。  如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例使用 C\# 建立包含泛型類型的元件，該元件具有在 [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)] 中撰寫泛型類型時不支援的特定條件約束。 如需詳細資訊，請參閱[類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
```  
// C3390.cs // compile with: /target:library // a C# program public class GR<C, V, N> where C : class where V : struct where N : new() {}  
```  
  
## 範例  
 下列範例會產生 C3390。  
  
```  
// C3390_b.cpp // compile with: /clr #using <C3390.dll> ref class R { R(int) {} }; value class V {}; ref struct N { N() {} }; int main () { GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type GR<R^, V, N^>^ gr2b;   // OK }  
```