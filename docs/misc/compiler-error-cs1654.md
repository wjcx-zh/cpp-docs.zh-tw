---
title: "編譯器錯誤 CS1654 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1654
無法修改 'variable' 的成員，因為它是「唯讀變數類型」  
  
 如果您嘗試修改唯讀變數 \(因為它在特殊建構中\) 的成員，會發生這個錯誤。  
  
 發生這種情況的其中一個常見區域是在 [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) 迴圈內。 它是編譯時期錯誤，需要修改集合項目的值。 因此，您無法修改為[實值類型](../Topic/Value%20Types%20\(C%23%20Reference\).md)的項目 \(包含[結構](../Topic/Structs%20\(C%23%20Programming%20Guide\).md)\)。 在項目為[參考類型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)的集合中，您可以修改每個項目的可存取成員，但任何加入、移除或取代完整項目的嘗試都會產生[Compiler Error CS1656](../Topic/Compiler%20Error%20CS1656.md)  
  
## 範例  
 下列範例會產生錯誤 CS1654，因為 `Book` 是 `struct`。 若要修正這個錯誤，請將 `struct` 變更為[類別](../Topic/class%20\(C%23%20Reference\).md)。  
  
```  
using System.Collections.Generic; using System.Text; namespace CS1654 { struct Book { public string Title; public string Author; public double Price; public Book(string t, string a, double p) { Title=t; Author=a; Price=p; } } class Program { List<Book> list; static void Main(string[] args) { //Use a collection initializer to initialize the list Program prog = new Program(); prog.list = new List<Book>(); prog.list.Add(new Book ("The C# Programming Language", "Hejlsberg, Wiltamuth, Golde", 29.95)); prog.list.Add(new Book ("The C++ Programming Language", "Stroustrup", 29.95)); prog.list.Add(new Book ("The C Programming Language", "Kernighan, Ritchie", 29.95)); foreach(Book b in prog.list) { //Compile error if Book is a struct //Make Book a class to modify its members b.Price +=9.95; // CS1654 } } } }  
  
```