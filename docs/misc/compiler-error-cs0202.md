---
title: "編譯器錯誤 CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0202
foreach 要求 'type.GetEnumerator\(\)' 的傳回類型 'type' 必須要有適合的公用 MoveNext 方法以及公用 Current 屬性  
  
 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 函式，用來啟用 foreach 陳述式的使用，無法傳回指標或陣列；它必須傳回可作為列舉值之類別的執行個體。 作為列舉值的適當需求包括公用 Current 屬性和公用 MoveNext 方法。  
  
> [!NOTE]
>  在 C\# 2.0 中，編譯器會自動為您產生 Current 和 MoveNext。 如需詳細資訊，請參閱[泛型介面](../Topic/Generic%20Interfaces%20\(C%23%20Programming%20Guide\).md) 中的程式碼範例。  
  
 下列範例會產生 CS0202：  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```