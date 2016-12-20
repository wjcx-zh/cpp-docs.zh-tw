---
title: "編譯器錯誤 CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0831
運算式樹狀結構不可包含基底存取  
  
 基底存取是指將通常為虛擬函式呼叫的函式呼叫，當做基底類型方法上的非虛擬函式呼叫來進行。 在運算式樹狀結構本身中不允許這麼做，但您可以在類別中叫用 Helper 方法來叫用基底類別方法。  
  
### 更正這個錯誤  
  
1.  如果您必須利用這種方式來存取基底類別方法，請建立呼叫基底類別的 Helper 方法，再由運算式樹狀結構呼叫此 Helper 方法。 下列程式碼說明這項技術。  
  
## 範例  
 下列範例會產生 CS0831：  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```