---
title: "編譯器錯誤 CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0425
方法 'method' 之類型參數 'type parameter' 的條件約束，必須符合介面方法 'method' 之類型參數 'type parameter' 的條件約束。 請考慮改用明確的介面實作。  
  
 如果覆寫衍生類別中的虛擬泛型方法，而且衍生類別中方法的條件約束不符合基底類別中方法的條件約束，則會發生這個錯誤。 若要避免這個錯誤，請確定兩個宣告中的 `where` 子句相同，或明確地實作介面。  
  
## 範例  
 下列範例會產生 CS0425：  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## 範例  
 條件約束不需要是常值相符項，只要這組條件約束的意義相同。 例如，下列就適用：  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```