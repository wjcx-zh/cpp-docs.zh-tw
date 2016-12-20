---
title: "編譯器錯誤 CS1545 | Microsoft Docs"
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
  - "CS1545"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1545"
ms.assetid: 56c377b5-4cf1-4c7d-b51d-463bad78f3ef
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1545
此語言不支援屬性、索引子或事件 'property'; 請試著直接呼叫存取子方法 'set accessor' 或 'get accessor'  
  
 程式碼正在使用的物件具有非預設的[索引子](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md)，並嘗試使用了索引的語法。 若要解決此錯誤，請呼叫屬性的 `get` 或 `set` 存取子方法。  
  
## 範例  
  
```  
// CPP1545.cpp // compile with: /clr /LD // a Visual C++ program using namespace System; public ref struct Employee { Employee( String^ s, int d ) {} property String^ name { String^ get() { return nullptr; } } }; public ref struct Manager { property Employee^ Report [String^] { Employee^ get(String^ s) { return nullptr; } void set(String^ s, Employee^ e) {} } };  
```  
  
## 範例  
 下列範例會產生 CS1545：  
  
```  
// CS1545.cs // compile with: /r:CPP1545.dll class x { public static void Main() { Manager Ed = new Manager(); Employee Bob = new Employee("Bob Smith", 12); Ed.Report[ Bob.name ] = Bob;   // CS1545 Ed.set_Report( Bob.name, Bob);   // OK } }  
```