---
title: "編譯器錯誤 CS0426 | Microsoft Docs"
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
  - "CS0426"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0426"
ms.assetid: 62df0deb-3624-436e-9691-ebe3ee1fc31f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0426
類型 'type' 中沒有類型名稱 'identifier'  
  
 當您參考的類型巢狀於另一個類型內，但此類型不存在時，就會發生這個錯誤。 如果您輸入的巢狀類型名稱不正確，就可能會發生這種情況。 請檢查使用的名稱拼字，並確認封入類型具有預期的成員。  
  
 下列範例會產生 CS0426，因為類別 C 沒有巢狀類型 A：  
  
```  
// CS0426.cs class C { // No nested types are declared. } class D { public static void Main() { C c = new C(); // Attempt to reference a nested type A: C.A a; // CS0426 because no such type C.A } }  
```  
  
## 請參閱  
 [類別和結構](../Topic/Classes%20and%20Structs%20\(C%23%20Programming%20Guide\).md)