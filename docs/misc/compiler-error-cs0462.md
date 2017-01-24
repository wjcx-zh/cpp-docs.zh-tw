---
title: "編譯器錯誤 CS0462 | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0462
繼承的成員 'member1' 和 'member2'，在類型 'type' 中有相同的簽章，所以無法覆寫  
  
 此錯誤是引用泛型所造成。 一般來說，類別中方法的兩個版本不能有相同的簽章。 但是，您可以使用泛型來指定可能會與另一種方法重複的泛型方法 \(如果是使用特定類型進行具現化\)。  
  
## 範例  
 具現化 `C<int>` 時，會使用相同的簽章建立方法 `F` 的兩個版本，因此類別 `D` 中的覆寫無法決定要套用覆寫的版本。  
  
 下列範例會產生 CS0462。  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```