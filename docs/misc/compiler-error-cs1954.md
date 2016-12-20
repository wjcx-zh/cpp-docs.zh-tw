---
title: "編譯器錯誤 CS1954 | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1954
無法使用集合初始設定式項目之最符合的多載方法 'method'。 集合初始設定式 'Add' 方法不能具有 ref 或 out 參數。  
  
 針對要使用集合初始設定式所初始化的集合類別，類別必須具有不是 `ref` 或 `out` 參數的 `public` `Add` 方法。  
  
### 更正這個錯誤  
  
-   如果您可以修改集合類別的原始程式碼，請提供未接受 `ref` 或 `out` 參數的 `Add` 方法。  
  
-   如果您無法修改集合類別，請使用它所提供的建構函式來進行初始化。 您無法將它與集合初始設定式搭配使用。  
  
## 範例  
 下列範例會產生 CS1954，因為 `MyList` 中 `Add` 清單的唯一可用多載具有 `ref` 參數。  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## 請參閱  
 [物件和集合初始設定式](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)