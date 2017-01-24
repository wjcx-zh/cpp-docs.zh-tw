---
title: "編譯器錯誤 CS0473 | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0473
明確介面實作 'method name' 符合多個介面成員。 實際選擇哪個介面成員視實作而定。 請考慮改用非明確的實作。  
  
 在某些情況下，泛型方法可能會取得和非泛型方法相同的特徵標記。 問題是在通用語言基礎結構 \(CLI\) 中繼資料系統中，無法明確描述哪個方法繫結至哪個位置。 它是根據 CLI 進行這項判斷。  
  
> [!NOTE]
>  Visual Studio 2008 發生這個錯誤的位置，在 Visual Studio 2005 中並未發生。  
  
### 更正這個錯誤  
  
1.  消除明確的實作，只讓隱含實作 `public int TestMethod(int)` 實作這兩個介面方法。  
  
## 範例  
 下列程式碼會產生 CS0473：  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## 請參閱  
 [編碼的奇妙旅程](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)