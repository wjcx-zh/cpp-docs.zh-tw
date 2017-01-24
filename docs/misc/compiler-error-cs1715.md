---
title: "編譯器錯誤 CS1715 | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1715
'Type1' : 類型必須是 'Type2' 以符合覆寫的成員 'MemberName'  
  
 這個錯誤與 [編譯器錯誤 CS0508](../misc/compiler-error-cs0508.md) 相同，只不過 CS0508 現在只適用於具有傳回類型的方法，而 CS1715 則適用於只有 'types' 沒有 'return types' 的屬性與索引子。  
  
## 範例  
 下列程式碼會產生 CS1715。  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```