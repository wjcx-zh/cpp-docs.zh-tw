---
title: "編譯器錯誤 CS0447 | Microsoft Docs"
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
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0447
屬性不能用在類型引數上，只能用在類型參數上  
  
 當您將屬性套用至發生在引動過程陳述式中的類型引數時，會發生這個錯誤。 它可以將屬性套用至類別或方法宣告陳述式中的類型參數，如下所示：  
  
```  
class C<[some attribute] T> {…}  
```  
  
 下行程式碼將產生這個錯誤。 假設定義於上行程式碼中的類別 `C` 具有稱為 `MyStaticMethod` 的靜態方法。  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## 範例  
 下列程式碼會產生錯誤 CS0447。  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```