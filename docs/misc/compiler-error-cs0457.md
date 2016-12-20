---
title: "編譯器錯誤 CS0457 | Microsoft Docs"
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
  - "CS0457"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0457"
ms.assetid: 5d5cf762-c817-4468-9455-59e966b8c140
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0457
從 'type name 1' 轉換為 'type name 2' 時，發現模稜兩可的使用者定義轉換 'Conversion method name 1' 和 'Conversion method name 2'  
  
 兩種轉換方法都適用，而且編譯器無法決定要使用哪一個。  
  
 下列任何一種情況都可能會造成這個錯誤：  
  
-   您想要將類別 A 轉換為類別 B，但類別 A 與 B 無關。  
  
-   A 衍生自 A0，而且沒有方法可從 A0 轉換為 B。  
  
-   B 具有子類別 B1，而且沒有方法可從 A 轉換為 B1。  
  
 編譯器將這兩種轉換方法視為相等，因為第一個轉換會提供最佳目的類型，而第二個轉換會提供最佳來源類型。 由於編譯器無法選擇，因此會產生這個錯誤。 若要解決錯誤，請撰寫將 A 轉換為 B 的新明確方法。  
  
 如果有兩個方法可將 A 轉換為 B，也可能會造成這個錯誤。若要修正錯誤，請透過明確轉換指定要使用的轉換。  
  
## 範例  
 下列範例會產生 CS0457。  
  
```  
// CS0457.cs using System; public class A { } public class G0 {  } public class G1<R> : G0 {  } public class H0 { public static implicit operator G0(H0 h) { return new G0(); } } public class H1<R> : H0 { public static implicit operator G1<R>(H1<R> h) { return new G1<R>(); } } public class Test { public static void F0(G0 g) {  } public static void Main() { H1<A> h1a = new H1<A>(); F0(h1a);   // CS0457 } }  
```