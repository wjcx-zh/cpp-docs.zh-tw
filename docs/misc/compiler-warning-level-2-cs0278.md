---
title: "編譯器警告 (層級 2) CS0278 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0278
'type' 未實作 'pattern name' 模式。 'method name' 與 'method name' 模稜兩可。  
  
 C\# 中有幾個依賴已定義模式的陳述式，例如 `foreach` 和 `using`。 例如，`foreach` 依賴實作「可列舉」模式的集合類別。  
  
 如果編譯器因為模稜兩可而無法比對，就可能發生 CS0278。 比方說，「可列舉」模式要求具有稱為 `MoveNext` 的方法，而您的程式碼可能包含稱為 `MoveNext` 的兩個方法。 編譯器會嘗試尋找一個介面來使用，但仍然建議您判斷並解決模稜兩可的原因。  
  
 如需詳細資訊，請參閱[如何：使用 foreach 存取集合類別](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0278：  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```