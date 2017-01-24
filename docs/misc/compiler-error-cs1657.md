---
title: "編譯器錯誤 CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1657
無法將 'parameter' 當做 ref 或 out 引數傳遞，因為 'reason'  
  
 在變數為唯讀的內容中，該變數當做 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 引數傳遞時，會發生這個錯誤。 唯讀內容包括 [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) 反覆運算變數、[using](../Topic/using%20Statement%20\(C%23%20Reference\).md) 變數和 `fixed` 變數。 若要解決這個錯誤，請不要在 `using` 區塊、`foreach` 陳述式和 `fixed` 陳述式中呼叫使用 `foreach`、`using` 或 `fixed` 變數作為 `ref` 或 `out` 參數的函式。  
  
## 範例  
 下列範例會產生 CS1657：  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## 範例  
 下列程式碼說明 `fixed` 陳述式中的相同問題：  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```