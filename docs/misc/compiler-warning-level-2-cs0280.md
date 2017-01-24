---
title: "編譯器警告 (層級 2) CS0280 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0280
'type' 未實作 'pattern name' 模式。 'method name' 的簽章錯誤。  
  
 C\# 中的兩個陳述式 \(**foreach** 和 **using**\) 分別使用預先定義的模式："collection" 和 "resource"。 編譯器因方法的簽章不正確而無法符合其中一個陳述式與其模式時，就會發生這個警告。 例如，"collection" 模式需要一個稱為 <xref:System.Collections.IEnumerator.MoveNext%2A> 的方法，這個方法未採用任何參數，並且會傳回 `boolean`。 您的程式碼可能包含具有參數或可能傳回物件的 <xref:System.Collections.IEnumerator.MoveNext%2A> 方法。  
  
 另一個範例是 "resource" 模式和 `using`。 "resource" 模式需要 <xref:System.IDisposable.Dispose%2A> 方法；如果您定義同名的屬性，則會收到這個警告。  
  
 若要解決這個警告，請確定類型中的方法簽章符合模式中對應方法的簽章，並確定您沒有與模式所需方法同名的屬性。  
  
## 範例  
 下列範例會產生 CS0280。  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```